
<template>
<div class="root">
  <p class="title">需要您填写如下信息，让我们帮您更好的推荐。</p>
  <mip-form method="get" url="http://mip.putibaby.com/update_ycq_ok" name="mip-form" class='mip_form'>
    <h4>您希望找：</h4>
    <table class="radio">
      <tr>
        <td>
          <div :class="{'checked': dateChecked,'unchecked':!dateChecked}" @click="date_checked"></div>
          <input type="radio" name="masterType" value="yuesao" checked>月嫂&nbsp;&nbsp;&nbsp;&nbsp;
          <span class="gray">在月子期间护理新生儿和产妇</span></td>
      </tr>
      <tr>
        <td>
          <div :class="{'checked': dateChecked,'unchecked':!dateChecked}" @click="date_checked"></div>
          <input type="radio" name="masterType" value="yuer">育儿嫂&nbsp;&nbsp;&nbsp;&nbsp;
          <span class="gray">为0-3岁幼儿提供照料和早教服务</span></td>
      </tr>
    </table>
    <p class="margin"> </p>
    <table class="name_table">
      <tr>
        <td>姓名：</td>
        <td><input type="text" name="name" class="name your_name" v-model="name" required="required" placeholder="请填写您的称呼"></td>
      </tr>
    </table>
    <table class="ycq_table">
      <tr>
        <td>宝宝生日\预产期：</td>
        <td><input type="date" name="ycq" class="name ycq" v-model="selectDate" required="required"></td>
      </tr>
    </table>
    <input type="submit" name="提交" class="submit" @click="handleSubmit_">
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
}

p {
  margin: 0px;
  padding: 0px;
  font-family: '黑体';
}

body {
  background-color: #fff;
  font-family: Arial, 'Hiragino Sans GB', 'Microsoft Yahei', '微软雅黑', '宋体', 宋体, Tahoma, Arial, Helvetica, STHeiti;
}

.root {
  /*padding-left: 10px;*/
}

.title {
  margin: 10px 10px 10px 10px;
  color: #333;
}

.gray {
  color: #666;
}

.name {
  /*width: 100px;*/
  border-radius: 5px;
  /*border: solid 1px #ddd !important;*/
}

table tr td {
  height: 30px;
}

.video_interview {
  display: block;
  width: 97%;
  height: 140px;
  margin-top: 20px;
  margin-bottom: 20px;
}

textarea {
  width: 97%;
  height: 100px;
  border-radius: 5px;
  color: #666;
  border: solid 1px #ddd !important;
  margin-top: 20px;
}

.submit {
  outline: none;
  -webkit-appearance: none;
  border-radius: 0;
  width: 97%;
  height: 44px !important;
  line-height: 20px;
  text-align: center;
  background-color: #afd03b !important;
  color: #fff !important;
  margin-top: 30px;
}

.margin {
  height: 10px;
  background-color: #f3f3f3;
  margin-left: -10px;
}

.mip_form {
  margin-left: 10px;
}

.name_table {
  border-bottom: solid 1px #ddd;
  width: 95%;
  margin-bottom: 10px;
}

.your_name {
  border: none !important;
  padding-left: 25px;
  font-size: 14px !important;

}

.ycq_table {
  border-bottom: solid 1px #ddd;
  width: 95%;
}

.ycq {
  background-color: #fff;
  border: none;
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


API.uploadFile = function(data, cb) {
  API.wrapRet_(
    '/api/upload_image', {
      'data': data,
      'target': 'media/image-[md5].jpg'
    },
    cb);
};


export default {
  mounted() {

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
    console.log(this);
    var pdata = JSON.parse(this.dataJsonstr);
    console.log('1111:', pdata);
    var data = pdata.order;

    return {
      rea: false,
      dateChecked: false;
      name: ,
      date: ,


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

    contract_location_change_() {
      contract_location = this.contract_location;
      this.saveIt_();
    },

    saveIt_() {

      // var data = this.props.data.order;
      var obj = {};

      obj.id = this.order.id;

      obj.contract_mama_id_card_list = this.contract_mama_id_card_zheng + ',' + this.contract_mama_id_card_fan;


      console.log('obj:', obj);
      API.wrapRet_(
        '/api/set_contract', obj,
        function(isOk, res) {
          console.log(res);
        });

    },

    handleSubmit_() {
      var pdata = JSON.parse(this.dataJsonstr);

      API.wrapRet_(
        '/api/submit_contract', {
          'id': this.order.id,
          'readonly': 1,
        },
        function(isOk, res) {
          console.log('res1111111:', res);
        });

    },


  }

}
</script>
