
<template>
<div class="root">
  <mip-form class="root" method="get" url="https://www.mipengine.org?we=123">
    <div class="warn">
      <span>尊敬的用户：</span><br>
      <span>为了能让菩提果的老师和月嫂更好的为您服务，需要您提供正确的手机号码：</span>
    </div>
    <div class="get">
      <input id="ph" class="ph" type="number" placeholder="请输入您的手机号码" v-model="phoneNumber" v-on:blur="changePhoneNumber_">
	  <!--<div id="err" class="err" v-if="errPhoneNumber">错误的手机号</div>-->
      <input id="code" class="code" type="number" placeholder="输入验证码" v-model="sms" v-on:blur="changeVerifySms_">
	  <!--<div id="smsSend" class="smsSend" @click="getVerify_" v-bind:disabled="smsDisable">获取验证码</div>-->
	  <input class="smsSend" type="button" @click="getVerify_" v-bind:disabled="smsDisabled" value="获取验证码"></input>
    </div>
    <div id="err" class="err" v-if="errSms">错误的验证码</div>
      <div id="err" class="err" v-if="errPhoneNumber">错误的手机号</div>
    <div class="submit">
      <input class="submitbtn" type="submit" value="确认提交" v-on:click="handleSubmit_" v-bind:disabled="subDisabled" />
    </div>
  </mip-form>
</div>
</template>


<style scoped>
.wrapper {
  margin: 0 auto;
  text-align: center;
}

* {
  margin: 0px;
  padding: 0px;
  width: 100%;
}

p {
  margin: 0px;
  padding: 0px;
  font-family: '黑体';
}

body {}

a {
  color: black !important;
  text-decoration: none !important;
}

a:checked {
  text-decoration: none !important;
}

a:visited {
  text-decoration: none !important;
}

a:hover {
  text-decoration: none !important;
}

.root {
  background: #fff;
  font-size: 14px;
}

.warn {
  color: rgba(102, 102, 102);
  padding: 10px;
  line-height: 2;
}

.get {
  margin-top: 10px;
  height: 100px;
  position: relative;
}
.get .btn1{
	position: relative;
    width: 42%;
    right: -228px;
    top: 49px;
    height: 38px;
border-radius:4px;
    border-style: none;
    background-color: #46ab49;
    color: #fff;
    text-align: center;

}

.ph {
  position: absolute;
  left: 10px;
  top: 0;
  display: block;
  border: 1px solid #ccc;
  border-radius: 2px;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  width: 94%;
}

.code {
  position: absolute;
  left: 10px;
  top: 50px;
  display: block;
  border: 1px solid #ccc;
  border-radius: 2px;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  width: 45%;
}

.err {
  color: red;
  margin: 10px;
  margin-top: 0px;
  height: 30px;
}

.smsSend {
  position: absolute;
  right: 10px;
  top: 50px;
  border-radius: 2px;
  line-height: 36px;
  text-align: center;
  background: #46AB49;
  color: #fff;
  cursor: pointer;
  width: 45%;
border-style:none;
}

.smsSend.disabled {
  pointer-events: none;
  cursor: default;
  opacity: 0.6;
}

.submit .submitbtn {
  background: #46AB49;
  color: #fff;
  cursor: pointer;
  line-height: 36px;
  text-align: center;
  border-radius: 4px;
  margin: 0 auto;
  width: 94%;
border-style:none;
left:3%;
position:relative;
}
</style>

<script>
var API = {};

function checkStatus(response) {
  if (response.status >= 200 && response.status < 300) {
    return response;
  } else {
    var error = new Error(response.statusText);
    error.response = response;
    throw error;
  }
}

function parseJSON(response) {
  return response.json()
}

API.wrapRet_ = function(api, opts, cb) {
  console.log('posting to ' + api);
  fetch(api, {
      method: 'POST',
      credentials: "same-origin",
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify(opts)
    })
    .then(checkStatus)
    .then(parseJSON)
    .then(ret => {
      if (ret.success) cb(true, ret.data);
      else cb(false, ret.error);
    })
    .catch(e => {
      console.error(e.message);
      cb(false, e.message);
    });
}


API.sendPhoneNumberVerifySms = function(phoneNumber, cb) {
  // if (!/^1\d{10}$/.test(phoneNumber)) {
  //   cb(false, '错误的手机号');
  //   return;
  // }

  API.wrapRet_(
    '/api/send_sms', {
      'phone_number': phoneNumber
    },
    cb);
}


API.sendPhoneNumberVerifySmsWithGt = function(phoneNumber, cb) {
  if (!/^1\d{10}$/.test(phoneNumber)) {
    cb(false, '错误的手机号');
    return;
  }

  // if (window.gt_loading) {
  //  setTimeout(function(){
  //      window.gt_loading = false;
  //  }, 100);
  //  return;
  // }

  var handler = function(captchaObj) {
    // captchaObj.appendTo('#captcha');
    captchaObj.onReady(function() {
      $("#wait").hide();
      captchaObj.verify();
    }).onSuccess(function() {
      var result = captchaObj.getValidate();
      if (!result) {
        return alert('请完成验证');
      }
      // window.gt_loading = false;
      API.wrapRet_(
        '/api/send_sms_validate', {
          'phone_number': phoneNumber,
          'geetest_challenge': result.geetest_challenge,
          'geetest_validate': result.geetest_validate,
          'geetest_seccode': result.geetest_seccode
        },
        cb);

    });

    window.captchaObj = captchaObj;

  };


  $.ajax({
    url: "/api/gt_register?t=" + (new Date()).getTime(),
    type: "get",
    dataType: "json",
    success: function(ret) {
      console.log(ret);
      var data = ret.data;

      initGeetest({
        gt: data.gt,
        challenge: data.challenge,
        offline: !data.success,
        new_captcha: data.new_captcha,

        product: "bind",
        width: "300px"
      }, handler);

    }
  });

}

API.verifyPhoneNumber = function(phoneNumber, sms, cb) {
  // if (!/^1\d{10}$/.test(phoneNumber)) {
  //   cb(false, '错误的手机号');
  //   return;
  // }
  //
  // if (!/^\d{4,6}$/.test(sms)) {
  //   cb(false, '错误的验证码');
  //   return;
  // }

  API.wrapRet_(
    '/api/verify_sms', {
      'phone_number': phoneNumber,
      'sms': sms
    }, cb);
}


export default {
  mounted() {
    console.log('This is my first custom component !')
  },
  firstInviewCallback() {
    this.init()
  },
  props: {
    src: {
      type: String,
      default: null
    },
    dataJsonstr: {
      type: String,
      default: null
    }
  },
  data() {
    console.log('data:',this);
    var pdata = JSON.parse(this.dataJsonstr);
    return {
      errPhoneNumber: false,
      errSms: false,
      phoneNumber: '',
      sms: '',
      smsDisabled: true,
      subDisabled: true,
    }
  },
  computed: {

  },
  methods: {
    init() {
      console.log('should loading');
      console.log(this.dataJson);
    },
    load_data() {
      console.log('should set data');
    },
    changePhoneNumber_() {
	  console.log('changePhone:',this);
      if (!/^1\d{10}$/.test(this.phoneNumber)) {
		console.log('phonenumber:',this.phoneNumber);
        this.errPhoneNumber = true;
        this.smsDisabled = true;
      } else {
        this.errPhoneNumber = false;
        this.smsDisabled = false;
      }
	  console.log('111111:',this);
    },
    changeVerifySms_() {
      if (!/^\d{4,6}$/.test(this.sms)) {
        this.errSms = true;
        this.subDisabled = true;
      } else {
        this.errSms = false;
        this.subDisabled = false;
      }
    },
    getVerify_() {
      // if (!/^1\d{10}$/.test(this.phoneNumber)) {
      //   this.errPh=true;
      //   return;
      // }
      API.sendPhoneNumberVerifySms(this.phoneNumber, function(isOk, res) {
        console.log(res);
      });
    },
    handleSubmit_() {

      API.verifyPhoneNumber(this.phoneNumber, this.sms, function(isOk, res) {
        console.log(res);
      });
      // window.location.href = '/master_card?mcode=' + fav.master.mcode;
    },
  }
}
</script>
