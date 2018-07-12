
<template>
<div class='root'>

  <div class="part" v-for="items in list">
    <div class="sub_head">
      <p>{{items.title}}</p>
    </div>
    <div class="item" v-for="it in items.list">
      <p for="it.id">
				{{it.title}}
      </p>
      <input type="checkbox" id="it.id" name="services" v-bind:disabled="rea" value="it.id" v-bind:checked="sk_c[it.id]" @click="changeChecked_(it.id,it.id)" v-on:change="Change_(it.id)"></input>

    </div>
  </div>

  <input class="mbtn" type="submit" value="提交" @click="submit_" v-show:disabled="!rea">


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
  padding-bottom: 15px;
  background: #f2f2f2;
  font-size: 14px;
  position: relative;
  width: 100%;
  color: #666;
  font-family: '黑体';
}

.main_head {
  height: 20px;
  margin-bottom: 15px;
}

.main_head p {
  position: relative;
  width: 80%;
  left: 15px;
}

.part {
  position: relative;
  width: 100%;
}

.sub_head {
  height: 44px;
  line-height: 44px;
  background: #f4f4f4;
  color: #999;
}

.sub_head p {
  position: relative;
  width: 50%;
  left: 15px;
  font-family: '黑体';
}

.item {
  position: relative;
  height: 44px;
  line-height: 44px;
  background: #fff;
}

.item p {
  display: inline;
  position: relative;
  left: 15px;
  font-family: '黑体';
}

.item input {
  position: absolute;
  right: 15px;
  width: 22px;
  height: 22px;
  top: 10px;
}

.mbtn {
  -webkit-appearance: none;
  background: #afd03b;
  color: #fff;
  width: 89.3%;
  line-height: 3px;
  border-radius: 5px;
  cursor: pointer;
  margin: 20px auto 10px auto;
  text-align: center;
  height: 47px;
  position: relative;
  left: 50%;
  margin-left: -44.65%;
  font-size: 18px;
  border-style: none;
}

.checked {
  background-image: url('/i/balance_checked.png');
  background-size: 22px 22px;
  width: 22px;
  height: 22px;
  top: 10px;
  right: 35px;
  position: absolute;
  z-index: 22;
}

.unchecked {
  background-image: url('/i/balance_unchecked.png');
  background-size: 22px 22px;
  width: 22px;
  height: 22px;
  top: 10px;
  right: 35px;
  position: absolute;
  z-index: 22;
}

input[type="checkbox"] {
  -webkit-appearance: none;
  background: #f4f4f4 url('/i/checkbox_22px.png');
  border-radius: 50%;
  border-style: none;
}

input[type="checkbox"]:checked {
  background-position: -22px 0;
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

API.saveIt_ = function(opts, cb) {
  API.wrapRet_(
    '/api/set_contract', {
      'contract_skill_req': opts.contract_skill_req,
      'id': opts.id,
      'order_id': opts.order_id,
    }, cb);
}


export default {
  beforeMount() {

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
    console.log('this', this);
    var pdata = JSON.parse(this.dataJsonstr);
    if (pdata.readonly != '1') {
      var readonly = false;
    } else {
      var readonly = true;
    }
    if (JSON.parse(this.dataJsonstr).contract_skill_req.indexOf(',') != -1) {
      var skill_list = JSON.parse(this.dataJsonstr).contract_skill_req.split(',');

    } else {
      var skill_list = [];
      skill_list.push(JSON.parse(this.dataJsonstr).contract_skill_req);
    }
    return {
      list: JSON.parse(this.dataJsonstr).list,
      check: false,
      contract_skill_req: [],
      skill_req: skill_list,
      sk_c: pdata.sk_c,
      rea: readonly,
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
    checked_(id) {
      return false;
    },
    Checked_(id) {
      this.checked_(id);
    },
    Change_(id) {},
    check_: function(id) {
      var self = this;
      var skill = this.skill_req.length;
      for (var i = 0; i < skill; i++) {
        if (id == this.skill_req[i]) {
          return true;
        } else {
          return false;
        }
      }
    },
    changeChecked_(id, state) {
      var self = this;
      var skill_list = this.skill_req;
      var skill_req = [];
      if (skill_list.indexOf(id.toString()) == -1) {
        skill_req = skill_list;
        skill_req.push(id.toString());

      } else {
        var skill_list_ = skill_list;
        var index = skill_list.indexOf(id.toString());
        var c = skill_list.splice(index, 1);
        for (var i = 0; i < skill_list_.length; i++) {
          if (skill_list_[i] == c[0]) {} else {
            skill_req.push(skill_list_[i]);
          }
        }
      }
      var skill_l = [];
      for (var i = 0; i < skill_req.length; i++) {
        if (skill_req[i] == '') {} else {
          skill_l.push(skill_req[i]);
        }
      }
      var opts = {};
      opts.id = JSON.parse(self.dataJsonstr).id;
      opts.contract_skill_req = skill_l.join(',');
      API.saveIt_(opts, function(isOk, res) {
        if (isOk) {
          console.log('success');
        }
      });
    },
    submit_() {
	  var url =  '/edit_contract?id=' + JSON.parse(this.dataJsonstr).id;
      // window.location.replace(url);
      window.MIP.viewer.open(url,{replace:true});
    },
  }
}
</script>
