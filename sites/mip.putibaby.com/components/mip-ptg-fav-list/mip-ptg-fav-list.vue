
<template>
<div class="row">
  <div v-for="order in list">
    <div class="root" @click="handleBtn(order)">
      <mip-img layout="responsive" width="85px" height="22px"
                  class="header" v-bind:src="order.master.header.small" ></mip-img>
      <!-- <img src={master.header.small} class="img"} /> -->
      <div class="name">{{ order.master.name }}</div>
      <div class="price">￥{{ order.master.price.ptg_price/100 }}</div>
      <div class="info">
        <mip-img layout="responsive" width="85px" height="22px"
                    class="age_img" src="i/age.png" ></mip-img>
        <span class="age">{{ order.master.age }}岁</span>
        <mip-img layout="responsive" width="85px" height="22px"
                    class="work_year_img" src="i/work_year.png" ></mip-img>
        <span class="work_year">{{ order.master.work_year }}年</span>
        <mip-img layout="responsive" width="85px" height="22px"
                    class="jiguan_img" src="i/jiguan.png" ></mip-img>
        <span class="jiguan">{{ order.master.jiguan }}</span>
      </div>
      <mip-img layout="responsive" width="85px" height="22px"
                    class="jt" src="i/jt-right.png" ></mip-img>
    </div>
    <div class="clear"></div>
  </div>
</div>  
</template>


<style scoped>
.wrapper {
  margin: 0 auto;
  text-align: center;
}

body{
   background-color: #f3f3f3 !important;
}
.row{
  background-color: #f3f3f3;
}
.root{
    background: #fff;
    position: relative;
    height: 72;
    overflow: hidden;
    cursor: pointer;
    margin-top: 10px;
  }

  .header{
    width: 50;
    height: 50;
    position: absolute;
    top: 10;
    left: 10;
    border-radius: 5;
  }

  .name{
    font-size:  16;
    font-weight: bold;
    color: #333;
    position: absolute;
    top: 15;
    left: 70;
  }

  .price{
    font-size:  16;
    font-weight: bold;
    color: red;
    position: absolute;
    top: 15;
    left: 130;
  }

  .info{
    font-size:  14;
    color: #666;
    position: absolute;
    top: 40;
    left: 70;
  }

  .icon{
    width: 14;
    position: relative;
    top: 0;
    display: inline-block;
    margin-right: 5;
  }

  .age{
    display: inline-block;
    margin-right: 10;
  }

  .work_year{
    display: inline-block;
    margin-right: 10;
  }

  .jt{
    position: absolute;
    right: 10;
    height: 20;
    top: 26;
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
  fetch(api,{  
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
    if(ret.success) cb(true, ret.data);
    else cb(false, ret.error);
  })  
  .catch(e => {
    console.error(e.message); 
    cb(false, e.message);
  });
}

API.rejectInterview = function(masterId, cb) {
  API.wrapRet_(
    '/api/reject_interview', 
    {
      'id': masterId
    },
    cb);
};



export default {
  mounted () {
    console.log('This is my first custom component !')
  },
   firstInviewCallback () {
    this.init()
  },
  props: {
    src: {
      type: String,
      default: null
    },
	dataJsonstr :{
	  type: String,
	  default: null
	  
	}        
  },
  data () {
	console.log(this);
	var pdata = JSON.parse(this.dataJsonstr);
    console.log(pdata.list);
    return {
		list: pdata.list,
		state: {
			showTuijianBtn:true
		}
    }
  },
  computed: {
    
  },
  methods: {
    init () {
      console.log('should loading');
      console.log(this.dataJson);
	  
    },

    load_data () {
      console.log('should set data');

    },

	  handleBtn(order){
      window.location.href = '/show_master?u=' + order.username;
    },

  }


}
</script>
