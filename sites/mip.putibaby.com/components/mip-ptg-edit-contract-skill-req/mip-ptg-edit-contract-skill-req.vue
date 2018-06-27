
<template>
<div class='root'>
  <mip-form method="get" url="https://www.mipengine.org?we=123">

    <div class="main_head">请勾选您认为重要的服务选项</div>

    <div class="part">
      <div class="sub_head">产妇护理</div>
      <div class="item">
        <p>产妇状态观察（恶露、伤口、子宫复旧）</p>
        <input type="checkbox" name="services" value="cf_zhuangtai" checked>
      </div>
      <div class="item">
        <p>母乳喂养指导</p>
        <input type="checkbox" name="services" value="cf_weiyang" checked>
      </div>
      <div class="item">
        <p>乳房护理</p>
        <input type="checkbox" name="services" value="cf_rufang" checked>
      </div>
      <div class="item">
        <p>协助擦浴</p>
        <input type="checkbox" name="services" value="cf_cayu" checked>
      </div>
      <div class="item">
        <p>保健按摩</p>
        <input type="checkbox" name="services" value="cf_anmo" checked>
      </div>
      <div class="item">
        <p>产后形体恢复</p>
        <input type="checkbox" name="services" value="cf_xingtihuifu" checked>
      </div>
      <div class="item">
        <p>产后恢复指导</p>
        <input type="checkbox" name="services" value="cf_chanhouhuifu" checked>
      </div>
    </div>

    <div class="part">
      <div class="sub_head">新生儿护理</div>
      <div class="item">
        <p>新生儿体温测量</p>
        <input type="checkbox" name="services" value="xsr_tiwen" checked>
      </div>
      <div class="item">
        <p>新生儿溢奶</p>
        <input type="checkbox" name="services" value="xsr_yinai" checked>
      </div>
      <div class="item">
        <p>新生儿湿疹</p>
        <input type="checkbox" name="services" value="qt_shizhen" checked>
      </div>
      <div class="item">
        <p>新生儿红臀护理</p>
        <input type="checkbox" name="services" value="qt_hongtun" checked>
      </div>
      <div class="item">
        <p>新生儿洗澡</p>
        <input type="checkbox" name="services" value="qt_xizao" checked>
      </div>
      <div class="item">
        <p>新生儿抚触</p>
        <input type="checkbox" name="services" value="qt_fuchu" checked>
      </div>
      <div class="item">
        <p>新生儿游泳</p>
        <input type="checkbox" name="services" value="qt_youyong" checked>
      </div>
      <div class="item">
        <p>脐带护理</p>
        <input type="checkbox" name="services" value="qt_qidai" checked>
      </div>
      <div class="item">
        <p>黄疸观察</p>
        <input type="checkbox" name="services" value="qt_huangdan" checked>
      </div>
      <div class="item">
        <p>“两便”护理</p>
        <input type="checkbox" name="services" value="qt_liangbian" checked>
      </div>
      <div class="item">
        <p>“三浴”护理</p>
        <input type="checkbox" name="services" value="qt_sanyu" checked>
      </div>
      <div class="item">
        <p>眼耳口鼻护理</p>
        <input type="checkbox" name="services" value="qt_koubi" checked>
      </div>
    </div>

    <div class="part">
      <div class="sub_head">婴儿护理</div>
      <div class="item">
        <p>母乳喂养指导</p>
        <input type="checkbox" name="services" value="yr_weiyang" checked>
      </div>
      <div class="item">
        <p>喂养用具指导</p>
        <input type="checkbox" name="services" value="yr_yongju" checked>
      </div>
      <div class="item">
        <p>大小便护理</p>
        <input type="checkbox" name="services" value="yr_daxiaobian" checked>
      </div>
      <div class="item">
        <p>物品消毒</p>
        <input type="checkbox" name="services" value="yr_xiaodu" checked>
      </div>
      <div class="item">
        <p>常见病预防</p>
        <input type="checkbox" name="services" value="yr_yufang" checked>
      </div>
      <div class="item">
        <p>换洗尿布/衣物</p>
        <input type="checkbox" name="services" value="yr_niaobu" checked>
      </div>
      <div class="item">
        <p>早期潜能开发</p>
        <input type="checkbox" name="services" value="yr_qianneng" checked>
      </div>
      <div class="item">
        <p>良好习惯养成</p>
        <input type="checkbox" name="services" value="yr_xiguan" checked>
      </div>
    </div>

    <div class="part">
      <div class="sub_head">其他服务</div>
      <div class="item">
        <p>产儿房间卫生</p>
        <input type="checkbox" name="services" value="qt_weisheng" checked>
      </div>
      <div class="item">
        <p>产儿衣物清洗</p>
        <input type="checkbox" name="services" value="qt_yiwu" checked>
      </div>
      <div class="item">
        <p>产后营养餐制作</p>
        <input type="checkbox" name="services" value="qt_yingyangcan" checked>
      </div>
      <div class="item">
        <p>营养配餐指导</p>
        <input type="checkbox" name="services" value="qt_peican" checked>
      </div>
    </div>

    <input class="mbtn" type="submit" value="提交">

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
  padding-bottom: 15px;
  background: #f2f2f2;
  font-size: 14px;
  position: relative;
  padding-left: 10px;
}

.main_head {
  height: 20px;
  margin-bottom: 15px;
}

.part {
  position: relative;
  margin-bottom: 20px;
}

.sub_head {
  height: 20px;
  background: #c0c0c0;
  margin-bottom: 10px;
}

.item {
  position: relative;
  margin: 5px auto;
}

.item p {
  display: inline;
}

.item input {
  position: absolute;
  right: 20px;
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
  position: relative;
  left: 50%;
  margin-left: -150px;
  font-size: 20px;
  border-style: none;
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
