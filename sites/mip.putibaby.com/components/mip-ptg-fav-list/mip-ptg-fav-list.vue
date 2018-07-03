
<template>
<div class="row">
  <div v-for="fav in favlist">
    <div class="root" @click="handleBtn(fav)">
      <mip-img layout="responsive" width="85px" height="22px"
                  class="header" v-bind:src="fav.master.header.small" ></mip-img>
      <!-- <img src={master.header.small} class="img"} /> -->
      <div class="name">{{ fav.master.name }}</div>
      <p class="starBox">
          <mip-img v-for="j in fav.master.star_1_list" layout="responsive" width="12" height="12"
           class="iconStar" src="/i/select_master_star.png" /></mip-img>
          <mip-img v-for="j in fav.master.star_0_list" layout="responsive" width="12" height="12"
           class="iconStar" src="/i/select_master_unstar.png" /></mip-img>
        </p>
      <div class="price">￥{{ fav.master.price.ptg_price/100 }}</div>
      <div class="info">
        <mip-img layout="responsive" width="12px" height="12px"
                    class="age_img" src="i/age.png" ></mip-img>
        <span class="age">{{ fav.master.age }}岁</span>
        <mip-img layout="responsive" width="12px" height="12px"
                    class="work_year_img" src="i/work_year.png" ></mip-img>
        <span class="work_year">{{ fav.master.work_year }}年</span>
        <mip-img layout="responsive" width="12px" height="12px"
                    class="jiguan_img" src="i/jiguan.png" ></mip-img>
        <span class="jiguan">{{ fav.master.jiguan }}</span>
      </div>
    </div>
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
  height:100%;
  padding: 10px;
  padding-top: 0px;
}
.root{
    background: #fff;
    position: relative;
    height: 68px;
    overflow: hidden;
    cursor: pointer;
    margin-top: 10px;
	 border:solid 1px #e5e5e5;
  }

  .header{
    width: 68px;
    height: 68px;
    position: absolute;
   
  }

  .name{
    font-size:  16px;
    color: #666;
    position: absolute;
    top: 15px;
    left: 80px;
  }

  .price{
    font-size:  16px;
    font-weight: bold;
    color: red;
    position: absolute;
    top: 15px;
    right: 20px;
  }

  .info{
    font-size:  14px;
    color: #666;
    position: absolute;
    top: 40px;
    left: 80px;
  }

  .icon{
    width: 14px;
    position: relative;
    top: 0px;
    display: inline-block;
    margin-right: 5px;
  }

  .age{
    display: inline-block;
    margin-right: 10px;
  }

  .work_year{
    display: inline-block;
    margin-right: 10px;
  }
 .age_img,.work_year_img,.jiguan_img{
 	width:12px!important;
	height:12px!important;
	display:inline-block;
 } 

 .starBox {
    position: absolute;
    left: 130px;
    top: 15px;
}
.starBox mip-img{
     width: 12px;
   height: 12px;
  display: inline-block;
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
    console.log(pdata.favlist);
    return {
		favlist: pdata.favlist,
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

	  handleBtn(fav){
      window.location.href = '/master_card?mcode=' + fav.master.mcode;
    },

  }


}
</script>
