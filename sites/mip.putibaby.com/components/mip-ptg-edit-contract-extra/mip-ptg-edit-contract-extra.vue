
<template>
<div class='root'>
  <textarea class="textarea" name="edit_contract_extra" validatetype="must" :readonly="rea" required placeholder="点击输入补充条款，如：上户遇节假日工资多倍结算/休息日约定；双胞胎加收金额；特殊上户要求等……" v-model="contract_extra" v-on:change='saveIt_'></textarea>
  <input class="mbtn" type="submit" value="提交" @click="submit_" v-show="!rea"></input>
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
  -webkit-appearance: none;
  position: relative;
  display: block;
  width: 92%;
  height: 300px;
  margin: 0px auto;
  border: 1px solid #e5e5e5;
  background: #fff;
  color: #666;
  line-height: 18px;
  font-size: 14px;
  border-radius: 5px;
  padding-top: 10px;
  padding-left: 10px;
  box-sizing: border-box;
}

.mbtn {
  -webkit-appearance: none;
  background: #afd03b;
  color: #fff;
  width: 89.3%;
  line-height: 3px;
  border-radius: 4px;
  cursor: pointer;
  margin: 30px auto 10px auto;
  text-align: center;
  height: 47px;
  position: absolute;
  left: 50%;
  margin-left: -44.65%;
  font-size: 18px;
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
  opts.mip_sid = API.sessionId || 'mip_sid_unknown';
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


API.saveIt_ = function(opts, cb) {
  API.wrapRet_(
    '/api/set_contract', {
      'contract_extra': opts.contract_extra,
      'id': opts.id,
      'order_id': opts.id,
    },
    cb);
}
export default {
  beforeMounted() {
    API.getExtra_();
  },
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
    if (pdata.readonly != '1') {
      var readonly = false;
    } else {
      var readonly = true;
    }
    if (pdata.readonly == '1' && pdata.contract_extra == '') {
      pdata.contract_extra = '无补充条款';
    }
    return {
      rea: readonly,
      contract_extra: pdata.contract_extra,
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
    saveIt_() {
      var self = this;
      var opts = {};
      opts.contract_extra = self.contract_extra;
      opts.id = JSON.parse(self.dataJsonstr).id;
      API.saveIt_(opts, function(isOk, res) {
        if (isOk) {
          console.log('success');
        } else {

        }
      });

    },
    submit_() {
      var self = this;
      var url = '/edit_contract?id=' + JSON.parse(self.dataJsonstr).id;
      // window.location.href = url;
      window.MIP.viewer.open(url,{replace:true});

    },
  }
}
</script>
