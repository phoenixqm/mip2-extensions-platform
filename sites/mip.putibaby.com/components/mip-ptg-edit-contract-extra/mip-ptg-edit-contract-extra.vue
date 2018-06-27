
<template>
<div class='root'>
  <mip-form method="get" url="https://www.mipengine.org?we=123">

    <textarea class="textarea" name="edit_contract_extra" validatetype="must" required placeholder="点击输入补充条款，如：上户遇节假日工资多倍结算/休息日约定；双胞胎加收金额；特殊上户要求等……"></textarea>

    <input class="mbtn" type="submit" value="提交">
    <!-- <div class="btn" >确定</div> -->

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
  padding-top: 20px;
  padding-bottom: 30px;
  background: #fff;
  font-size: 14px;
  position: relative;
}

.textarea {
  display: block;
  width: 80%;
  height: 300px;
  margin: 10px auto;
  border: 1px solid #ccc;
  background: #fff;
  color: #333;
  line-height: 18px;
}

.mbtn {
  background: #FF6867;
  color: #fff;
  width: 300px;
  line-height: 3px;
  border-radius: 4px;
  cursor: pointer;
  margin: 20px auto 10px auto;
  text-align: center;
  height: 45px;
  position: absolute;
  left: 50%;
  margin-left: -150px;
  font-size: 20px;
  border-style: none;
}

.btn {
  background: #FF6867;
  color: #fff;
  width: 300px;
  line-height: 40px;
  border-radius: 4px;
  cursor: pointer;
  margin: 20px auto 10px auto;
  text-align: center;
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
    console.log('data:', this);
    var pdata = JSON.parse(this.dataJsonstr);
    return {


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

    },
  }
}
</script>
