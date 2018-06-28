
<template>
<div class='root'>
  <mip-form method="get" url="https://www.mipengine.org?we=123">

    <div class="main_head">请勾选您认为重要的服务选项</div>
	<div class="part" v-for="items in list">
	  <div class="sub_head">{{items.title}}</div>
      <div class="item" v-for="it in items.list">
		<p>{{it.title}}</p>
        <input type="checkbox" name="services" value="it.title" v-bind:checked="check" @click="changeChecked_(it.id,it.id)" >
      </div>
	</div>
	<!--
    <div class="part">
	  <div class="sub_head">产妇护理</div>
      <div class="item">
        <p>产妇状态观察（恶露、伤口、子宫复旧）</p>
        <input type="checkbox" name="services" value="cf_zhuangtai" :checked="cf_zhuangtai">
      </div>
      <div class="item">
        <p>母乳喂养指导</p>
        <input type="checkbox" name="services" value="cf_weiyang" :checked="cf_weiyang">
      </div>
      <div class="item">
        <p>乳房护理</p>
        <input type="checkbox" name="services" value="cf_rufang" :checked="cf_rufang">
      </div>
      <div class="item">
        <p>协助擦浴</p>
        <input type="checkbox" name="services" value="cf_cayu" :checked="cf_cayu">
      </div>
      <div class="item">
        <p>保健按摩</p>
        <input type="checkbox" name="services" value="cf_anmo" :checked="cf_anmo">
      </div>
      <div class="item">
        <p>产后形体恢复</p>
        <input type="checkbox" name="services" value="cf_xingtihuifu" :checked="cf_xingtihuifu">
      </div>
      <div class="item">
        <p>产后恢复指导</p>
        <input type="checkbox" name="services" value="cf_chanhouhuifu" :checked="cf_chanhouhuifu">
      </div>
    </div>

    <div class="part">
      <div class="sub_head">新生儿护理</div>
      <div class="item">
        <p>新生儿体温测量</p>
        <input type="checkbox" name="services" value="xsr_tiwen" :checked="xsr_tiwen">
      </div>
      <div class="item">
        <p>新生儿溢奶</p>
        <input type="checkbox" name="services" value="xsr_yinai" :checked="xsr_yinai">
      </div>
      <div class="item">
        <p>新生儿湿疹</p>
        <input type="checkbox" name="services" value="xsr_shizhen" :checked="xsr_shizhen">
      </div>
      <div class="item">
        <p>新生儿红臀护理</p>
        <input type="checkbox" name="services" value="xsr_hongtun" :checked="xsr_hongtun">
      </div>
      <div class="item">
        <p>新生儿洗澡</p>
        <input type="checkbox" name="services" value="xsr_xizao" :checked="xsr_xizao">
      </div>
      <div class="item">
        <p>新生儿抚触</p>
        <input type="checkbox" name="services" value="xsr_fuchu" :checked="xsr_fuchu">
      </div>
      <div class="item">
        <p>新生儿游泳</p>
        <input type="checkbox" name="services" value="xsr_youyong" :checked="xsr_youyong">
      </div>
      <div class="item">
        <p>脐带护理</p>
        <input type="checkbox" name="services" value="xsr_qidai" :checked="xsr_qidai">
      </div>
      <div class="item">
        <p>黄疸观察</p>
        <input type="checkbox" name="services" value="xsr_huangdan" :checked="xsr_huangdan">
      </div>
      <div class="item">
        <p>“两便”护理</p>
        <input type="checkbox" name="services" value="xsr_liangbian" :checked="sxr_liangbian">
      </div>
      <div class="item">
        <p>“三浴”护理</p>
        <input type="checkbox" name="services" value="xsr_sanyu" :checked="xsr_sanyu">
      </div>
      <div class="item">
        <p>眼耳口鼻护理</p>
        <input type="checkbox" name="services" value="xsr_koubi" :checked="qt_koubi">
      </div>
    </div>

    <div class="part">
      <div class="sub_head">婴儿护理</div>
      <div class="item">
        <p>母乳喂养指导</p>
        <input type="checkbox" name="services" value="yr_weiyang" :checked="yr_weiyang">
      </div>
      <div class="item">
        <p>喂养用具指导</p>
        <input type="checkbox" name="services" value="yr_yongju" :checked="yr_yongju">
      </div>
      <div class="item">
        <p>大小便护理</p>
        <input type="checkbox" name="services" value="yr_daxiaobian" v-bind:checked="yr_daxiaobian">
      </div>
      <div class="item">
        <p>物品消毒</p>
		<input type="checkbox" name="services" value="yr_xiaodu" v-bind:checked="yr_xiaodu">
      </div>
      <div class="item">
        <p>常见病预防</p>
        <input type="checkbox" name="services" value="yr_yufang" v-bind:checked="yr_yufang">
      </div>
      <div class="item">
        <p>换洗尿布/衣物</p>
        <input type="checkbox" name="services" value="yr_niaobu" v-bind:checked="yr_niaobu">
      </div>
      <div class="item">
        <p>早期潜能开发</p>
        <input type="checkbox" name="services" value="yr_qianneng" v-bind:checked="yr_qianneng">
      </div>
      <div class="item">
        <p>良好习惯养成</p>
        <input type="checkbox" name="services" value="yr_xiguan" v-bind:checked="yr_xiguan">
      </div>
    </div>

    <div class="part">
      <div class="sub_head">其他服务</div>
      <div class="item">
        <p>产儿房间卫生</p>
        <input type="checkbox" name="services" value="qt_weisheng" v-bind:checked="qt_weisheng">
      </div>
      <div class="item">
        <p>产儿衣物清洗</p>
        <input type="checkbox" name="services" value="qt_yiwu" v-bind:checked="qt_yiwu">
      </div>
      <div class="item">
        <p>产后营养餐制作</p>
        <input type="checkbox" name="services" value="qt_yingyangcan" v-bind:checked="qt_yingyangcan">
      </div>
      <div class="item">
        <p>营养配餐指导</p>
        <input type="checkbox" name="services" value="qt_peican" v-bind:checked="qt_peican">
      </div>
    </div>
	-->

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
  width:100%;
}

.main_head {
  height: 20px;
  margin-bottom: 15px;
}

.part {
  position: relative;
  margin-bottom: 20px;
  width:100%;
}

.sub_head {
  height: 20px;
  background: #c0c0c0;
  margin-bottom: 10px;
}

.item {
  position: relative;
  margin: 5px auto;
  height:18px;
}

.item p {
  display: inline;
}

.item input {
  position: absolute;
  right: 20px;
  width:5%;
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
  margin-left: -160px;
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

API.getSkillList = function(cb){
	API.wrapRet_(
	'/api/get_skill_list',{},cb);
	
}
API.verifyPhoneNumber = function(phoneNumber, sms, cb) {
  API.wrapRet_(
    '/api/verify_sms', {
      'phone_number': phoneNumber,
      'sms': sms
    }, cb);
}


export default {
  beforeMount(){
	var self =this;
	API.getSkillList(function(isOk,res){
	console.log('re1111111111111111111111s',res);
	self.list=res.list;
	});
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

    return {
		list:list,
		count:0,
		check:false,
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
	changeChecked_(id,state) {
	console.log(333333333333333333);
	console.log(id);
	var cc = 0;
	

	},

  }
}
</script>
