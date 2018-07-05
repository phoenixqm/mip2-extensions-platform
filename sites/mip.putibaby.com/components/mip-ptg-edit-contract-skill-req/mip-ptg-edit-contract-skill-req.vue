
<template>
<div class='root'>

	<div class="part" v-for="items in list">
	  <div class="sub_head"><p>{{items.title}}</p></div>
      <div class="item" v-for="it in items.list">
		<p>			<label for="it.id">
				{{it.title}}
			</label>
		</p>
		<input type="checkbox" id="it.id" name="services" v-bind:disabled="rea" value="it.id" v-bind:checked="sk_c[it.id]"  @click="changeChecked_(it.id,it.id)" v-on:change="Change_(it.id)"></input>
		<!--	<div :class="{'checked': checked_(it.id),'unchecked': !checked_(it.id)}" @click="Check_(it.id)"></div>	-->
	

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
  width:100%;
  color:#666;
  font-family:'黑体';
}

.main_head {
  height: 20px;
  margin-bottom: 15px;
}
.main_head p{
position:relative;
width:80%;
left:15px;
}

.part {
  position: relative;
  width:100%;
}

.sub_head {
  height: 44px;
  line-height: 44px;
  background: #f4f4f4;
  color:#999;
}
.sub_head p {
  position: relative;
  width:50%;
  left:15px;
  font-family:'黑体';
}

.item {
  position: relative;
  height:44px;
  line-height:44px;
  background: #fff;
}

.item p {
  display: inline;
  position:relative;
  left: 15px;
  font-family:'黑体';
}

.item input {
  position: absolute;
  right: 15px;
  width:22px;
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
  position:absolute;
  z-index:22;
}
.unchecked {
  background-image: url('/i/balance_unchecked.png');
  background-size: 22px 22px;
  width: 22px;
  height: 22px;
  top: 10px;
  right: 35px;
  position:absolute;
  z-index:22;
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
  beforeMount(){

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
console.log('this',this);
var pdata = JSON.parse(this.dataJsonstr);
if(pdata.readonly!='1'){
var readonly=false;
}else{
var readonly=true;
}
	if(JSON.parse(this.dataJsonstr).contract_skill_req.indexOf(',')!= -1){
	var skill_list = JSON.parse(this.dataJsonstr).contract_skill_req.split(',');

	}else{
	var skill_list = [];
	skill_list.push(JSON.parse(this.dataJsonstr).contract_skill_req);
	}
    return {
		list:JSON.parse(this.dataJsonstr).list, 
		check:false,
		contract_skill_req:[],
		skill_req:skill_list,
		sk_c:pdata.sk_c,
		rea:readonly,
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
	  //console.log('222222dd22:',id);
	  return false;
	
	},
	Checked_(id) {
	  console.log('333333333');
	 this.checked_(id);
	},
	Change_(id) {
	  console.log('id:',id);
	console.log('....:',this);
	},
	check_: function(id){
	  var self=this;
	  console.log('23',this.skill_req);
		var skill = this.skill_req.length;
		for (var i =0;i < skill; i++){
		  if(id == this.skill_req[i] ){
		  return true;
		}else {
		return false;}
	  }
	},
	changeChecked_(id,state) {
	  var self =this;
	  var skill_list =this.skill_req;
var skill_req = [];
if(skill_list.indexOf(id.toString()) == -1){
  skill_req=skill_list;
	skill_req.push(id.toString());

}else{
  var skill_list_ = skill_list;
	var index = skill_list.indexOf(id.toString());
	var c = skill_list.splice(index,1);
	for(var i=0;i<skill_list_.length;i++){
		if(skill_list_[i] == c[0]){
		}else{
			skill_req.push(skill_list_[i]);
		}
	}
}
var skill_l=[];
for(var i=0;i<skill_req.length;i++){
  if(skill_req[i]==''){}else{
  	skill_l.push(skill_req[i]);
  }
}



	  var  opts ={};
	  opts.id = JSON.parse(self.dataJsonstr).id;
	  opts.contract_skill_req = skill_l.join(',');
	  console.log('opts:',opts.contract_skill_req);
	API.saveIt_(opts,function(isOk,res){
	  if(isOk){
		console.log('success');
	  }
	});
	
	},
	submit_(){
	  window.location.href='/edit_contract?id='+ JSON.parse(this.dataJsonstr).id;
	},
	
  }
}
</script>
