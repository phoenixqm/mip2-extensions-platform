<template>
  <div class="wrapper">
  <div class="top_level_1">
        <mip-carousel
        autoplay
        defer="3000"
        width=400
        height=277
        layout="responsive"
        indicatorId="mip-carousel-example"
        >
          <mip-img src="/i/b1.png"></mip-img>
          <mip-img src="/i/b2.png"></mip-img>
          <mip-img src="/i/b3.png"></mip-img>
        </mip-carousel>
        <div class="mip-carousel-indicator-wrapper">
            <div class="mip-carousel-indicatorDot" id="mip-carousel-example">
                <div class="mip-carousel-activeitem mip-carousel-indecator-item"></div>
                <div class="mip-carousel-indecator-item"></div>
                <div class="mip-carousel-indecator-item"></div>
                <div class="mip-carousel-indecator-item"></div>
            </div>
        </div>
  </div>
  <div>
    <a href="/coupon" mip-link>
      <mip-img src="/i/yhq_jt.png"></mip-img>
    </a>  
  </div>
  <div>
    <div class="find">
      <a href="/select_master" mip-link>
        <mip-img src="/i/find_ys.png"></mip-img>
      </a>
    </div>
    <div class="help">  
      <a href="/update_ycq_mip" mip-link>
        <mip-img src="/i/help_me.png"></mip-img> 
      </a>
    </div>  
  </div>
  
  <div class="bottom">
    <a class="bottom_left" href="tel:4006188835">
      <mip-img src="/i/index_phone.png" width="132px" height="22px" class="bottom_left_img"></mip-img>
    </a>
    <a @click="handleOrderList"><mip-img src="/i/ind_person.png" width="38px" height="25px" class="bottom_right_img"></mip-img></a>
  </div>

  </div>
</template>

<style scoped>
.wrapper {
  margin: 0 auto;
  text-align: center;
}

    /* <!-- index.css --> */
      p{
        margin: 0px;
        padding: 0px;
        font-family: '黑体';
      }
    /* <!-- banner.css --> */     
      .top_level_1{
        width: 100%;
        position: relative;
      }
      
      mip-form form {
        position: relative;
        left: 0px;
        width: 90vw;
      }
      mip-form input[type='text'] {
        padding-right: 30px;
        width: 80%;
        margin: auto;
        position: relative;
        top: 20px;
        background-color: rgba(0,0,0,0);
      }

      mip-form input[type='submit'] {
        border: 1px solid #fe7834;
        border-radius: 5px;
        color: #333;
        background-color: #fe7834;
        width: 98%;
        margin: auto;
        position: relative;
        top: 40px;
      }
      mip-carousel{
        width: 100%;
        height: 73.8%;
      }
      .mip-carousel-indicator-wrapper {
        text-align: center;
        background-color: rgba(0,0,0,.0);
        position: absolute;
        top: 130px;
        left: 190px;
      }
      .mip-layout-container {
        /* display: block; */
        position: relative;
        display: inline-block;
        width: 100%;
        margin: auto;
      }
      .mip-login-container {
		display:inline-block;
	  }
	  .test-login-div {
		margin-bottom: 130px;
	  }
      mip-form div {
        display: none;
        color: #ec1f5c;
        font-size: 12px;
        text-align: left;
        padding: 0 10% 0 3%;
        position: relative;
        left: 30px;
        top: 28px;
      }
      
      .find{
        width: 44%;
        margin-left: 4%;
        margin-right: 2%;
        height: 150px;
        text-align: center;  
        float: left;    
      }

      .help{
        width: 44%;
        margin-left:2%;
        margin-right: 4%;
        height: 150px;
        text-align: center;  
        float: left;    
      }

      
      .bottom{
        position: fixed;
        bottom: 0;
        height: 45px;
        line-height: 45px;
        background-color: #fff;
        width: 100%;
		z-index:9999;
      }
      
      .bottom_left{
        width: 85%;
        height: 45px;
        text-align: center;
        display: inline-block;
        color: black;
        padding-left:20%;
      }
      
      .bottom_left_img{
        vertical-align: -6px;
      }
      .bottom_right_img{
        vertical-align: -6px;
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
  opts.mip_sid = API.sessionId || '';
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

export default {
  mounted () {
    console.log('This is index component !');
    var self = this;
    this.$element.customElement.addEventAction('logindone', event => {
      // 这里可以输出登录之后的数据

      // 获取用户信息
      console.log(event);
      API.sessionId = event.sessionId;

      self.$set(self, 'isLogin', true);
      self.$set(self, 'isUnion', event.userInfo.isUnion);
     
      if (event.userInfo.isUnion && API.next_cmd == 'order_list') {
        console.log('logindone to order_list');
        window.MIP.viewer.open('order_list', {});
        API.next_cmd = '';
      } else if (event.userInfo.isUnion && API.next_cmd == 'coupon') {
        console.log('logindone to coupon');
        window.MIP.viewer.open('coupon', {});
        API.next_cmd = '';        
      } else if (!event.userInfo.isUnion) {
        console.log('logindone to submit_ph');
        window.MIP.viewer.open('/submit_ph?to=' + encodeURIComponent(window.location.href), {});
      }

    });
  },

  props: {
    dataJsonstr :{
      type: String,
      default: null
    }
  },
  data () {
    console.log(this);
    // var pdata = JSON.parse(this.dataJsonstr);
    return {
      // data: pdata.data,
      isLogin:false,
      isUnion:false
    }
  },
  computed: {
    
  },
  methods: {
    init () {
      console.log('should loading');

    },
    created() {

    },

    checkLogin_(cmd) {

      if (!this.isLogin){
        API.next_cmd = cmd;
        this.$emit('login');
        return false;
      }
  
      return true;
    },

  reload_() {
    console.log('reloading');
  },
  handleCoupon(){
    console.log('handleCoupon');
    if (!this.checkLogin_('coupon')) 
      return;
    window.MIP.viewer.open('/coupon ', {});
  },
  handleOrderList(){
    console.log('handleOrderList');
    if (!this.checkLogin_('order_list')) 
      return;
    window.MIP.viewer.open('/order_list ', {});
  },
    load_data () {
      console.log('should set data');
    }
  }

}
</script>
