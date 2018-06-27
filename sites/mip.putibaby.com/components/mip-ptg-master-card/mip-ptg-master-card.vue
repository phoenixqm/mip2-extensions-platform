
<template>
<div class="root">
  <div class="masterShow">
    <div>
      <div class="mS_headerBorder">
        <mip-img layout="responsive" width="50px" height="50px"
         class="mS_header" :src="data.info.header.small"></mip-img>
      </div>
      <div class="mS_info">
        <p class="mS_masterName">{{ data.info.name }}</p>
         <div class="starBox">
              <mip-img v-for="s in data.shanghu_data.star_1_list" layout="responisve" width="12px" height="12px" class="iconStar" src="/i/select_master_star.png" ></mip-img>
        </div>
        <p class="mC_Des">
          <span>
            {{ data.info.description[0] }}
          </span>
          <span>
            {{ data.info.description[1] }}
          </span>
          <span>
            {{ data.info.description[2] }}
          </span>
        </p>
        
      </div>
    </div>
  </div>

  <div class="fuwu">
      <p class="expectCity">
          服务报价：￥<span class="red">{{ data.info.price.ptg_price/100 }}</span>元
      </p>
      <p class="expectCity">服务区域：{{ data.info.expect_city }}</p>
  </div>

  <div class="jieshao">
      <div class="pJC_head">
          <mip-img layout="responisve" width="12px" height="12px"
            src="i/card_circle_1.png" ></mip-img>
          <span>自我介绍</span>
      </div>    
      <mip-showmore maxheight='40' animatetime='.3' id="showmore01">
           <div class="jieshao_content">{{ data.info.my_intro }}</div>
      </mip-showmore>
      <div on="tap:showmore01.toggle" data-closetext="收起" class="mip-showmore-btn">展开</div>
  </div>


  <div v-if="data.info.offer_service" class="serverCard">
    <!--  <a href="https://h5.putibaby.com/999.999/master/watch_service_details?u=<%= m.info.username %>"> -->
      <div class="sC_head">
        <mip-img layout="responisve" width="12px" height="12px"
          src="i/card_circle_1.png" ></mip-img>
        <span>月嫂服务项目</span>
        <!--  <span>查看更多&nbsp;<mip-img layout="responisve" width="8px" height="14px" src="i/right_white.png" ></mip-img></span> -->
      </div>
    <!-- </a> -->
    <table>
      <tbody>
        <tr>
          <td>{{ data.skill_list[0].title }}<br />{{ data.skill_list[0].ok_cc }}</td>
          <td>{{ data.skill_list[1].title }}<br />{{ data.skill_list[1].ok_cc }}</td>
          <td>{{ data.skill_list[2].title }}<br />{{ data.skill_list[2].ok_cc }}</td>
          <td>{{ data.skill_list[3].title }}<br />{{ data.skill_list[3].ok_cc }}</td>
        </tr>
      </tbody>
    </table>
  </div>


  <div v-if="data.info.price_yuer.market_price > 0 || data.info.price_yuer.market_halfday_price > 0" class="serverCard">
    <!-- <a href="https://h5.putibaby.com/999.999/master/watch_yuer_service_details?u={{ data.info.username }}"> -->
      <div class="sC_head">
        <mip-img layout="responisve" width="12px" height="12px"
          src="i/card_circle_1.png" ></mip-img>
        <span>育儿嫂服务项目</span>
        <!-- <span>查看更多&nbsp;<mip-img layout="responisve" width="8px" height="14px" src="i/right_white.png" ></mip-img></span> -->
      </div>
    <!-- </a> -->
    <table>
      <tbody>
        <tr>
          <td>{{ data.skill_list_yuer[0].title }}<br />{{ data.skill_list_yuer[0].ok_cc }}</td>
          <td>{{ data.skill_list_yuer[1].title }}<br />{{ data.skill_list_yuer[1].ok_cc }}</td>
          <td>{{ data.skill_list_yuer[2].title }}<br />{{ data.skill_list_yuer[2].ok_cc }}</td>
          <td>{{ data.skill_list_yuer[3].title }}<br />{{ data.skill_list_yuer[3].ok_cc }}</td>
        </tr>
      </tbody>
    </table>
   
  </div>

  <div class="albumCard">
    <!-- <a href="https://h5.putibaby.com/999.999/master/dgxc?u=<%= m.info.username %>"> -->
      <div class="aC_head">
        <mip-img layout="responisve" width="12px" height="12px"
          src="i/card_circle_1.png" ></mip-img>
        <span>相册</span>
        <!-- <span>查看相册&nbsp;<mip-img layout="responisve" width="8px" height="14px" src="i/right_white.png" ></mip-img></span> -->
      </div>
    <!-- </a> -->
    <div class="picList">
      <p v-if="data.xc_list.length == 0">没有照片</p>
      <div v-if="data.xc_list.length > 0">
          <mip-img v-for="pic in data.xc_list" layout="responsive" popup width="70px" height="70px"
           :src="pic.small" ></mip-img>            
      </div>

    </div>
  </div>

  <div class="pingJiaCard">
      <!--  <a href="https://h5.putibaby.com/999.999/master/watch_shanghu_details?u=<%= m.info.username %>"> -->
      <div class="pJC_head">
        <mip-img layout="responisve" width="12px" height="12px"
          src="i/card_circle_1.png" ></mip-img>
        <span>客户评价</span>
       <!--  <span>共<%= m.shanghu_data.cc %>条评价&nbsp;<mip-img layout="responisve" width="8px" height="14px" src="i/right_white.png" ></mip-img></span> -->
      </div>
    <!-- </a> -->
    <div class="pingJia">

      <p v-if="data.shanghu_data.cc == 0" >没有评价</p>
      <div v-else>
        <table>
          <tbody>
           <!--  <tr>
              <td>
                综合评价
                <div class="starBox">
                  <% for(var j = 0;j < Math.round(m.shanghu_data.feedback_total_star/m.shanghu_data.feedback_cc); j++) {%>
                    <mip-img layout="responisve" width="12px" height="12px" class="iconStar" src="/i/select_master_star.png" ></mip-img>
                  <%}%>
                  <% for(var j = 0;j < 5 - Math.round(m.shanghu_data.feedback_total_star/m.shanghu_data.feedback_cc); j++) {%>
                    <mip-img layout="responisve" width="12px" height="12px" class="iconStar" src="/i/select_master_unstar.png" ></mip-img>
                  <%}%>
                </div>
              </td>
            </tr> -->
            <!-- <tr>
              <td>
                <span><%= m.last_feedback.shanghu_at %></span>
                <span>至</span>
                <span><%= m.last_feedback.end_at %></span>
                <span class="left">共<%= m.last_feedback.days %>天</span>
              </td>
            </tr> -->
            <!-- <tr>
              <td class="customer">
                <mip-img layout="responisve" width="50px" height="50px" src="<%= m.last_feedback.mama_info.header.small %>" ></mip-img>
                <div class="customerInfo">
                  <p>
                    <span><%= m.last_feedback.mama_info.name %> &nbsp;<%= m.last_feedback.mama_info.role %>(<%= m.last_feedback.mama_info.type=='history' ? '历史客户' : '菩提果签约' %>
                    <%= m.last_feedback.mama_info.master_type == 'yuer' ? '育儿单' : '月嫂单' %>
                    )
                    </span>
                  </p>
                  <p>手机：<%= m.last_feedback.mama_info.phone_number %></p>
                </div>
              </td>
            </tr> -->
            <!-- <tr>
              <td>
                <span>拍照:<%= m.last_feedback.record_cc %>张</span>
                <span class="left">护理记录:<%= m.last_feedback.care_cc %></span>
              </td>
            </tr> -->
            <tr>
              <td class="customerEvaluate">
                <!-- <p class="cE_title">客户评价</p> -->
                <p class="cE_article">
                  {{ data.last_feedback.feedback.comment }}
                </p>
                  <mip-img v-for="p in data.last_feedback.feedback.pics" layout="responisve" width="50px" height="50px" :src="p.small" ></mip-img>
              </td>
            </tr>
          </tbody>
        </table>

      </div>
    </div>
  </div>


  <table class="tbl" cellspacing="0">
      <tbody>
          <tr>
              <td class="td1">
                  <a class="a" href='tel:400-618-8835'>
                      <mip-img layout="responisve" width="38px" height="32px" src="i/card_ph.png" ></mip-img>
                  </a>
              </td>
              <td class="td-fav" @click="this.handleFav">
                  <a class="a">
                      <mip-img v-if="data.info.isfav" layout="responisve" width="29px" height="35px" src="i/has_fav.png" ></mip-img>
                      <mip-img v-else-if="!data.info.isfav" layout="responisve" width="21px" height="35px" src="i/un_fav.png" ></mip-img>
                      <mip-img v-else layout="responisve" width="21px" height="35px" src="i/un_fav.png" ></mip-img>
                  </a>
              </td>                    

              <td v-if="data.info.can_online_interview" class="td2">
                  <a :href="'/update_time?mcode=' + data.codeid">预约视频面试</a>
              </td>

              <td v-else class="td2">
                  <a :href="'/order_list?mcode=' + data.codeid">{{ data.info.order_desc_str }}-查看预约</a>
              </td> 
              
          </tr>
      </tbody>
  </table>

</div>
    

</template>


<style scoped>
.wrapper {
  margin: 0 auto;
  text-align: center;
}

*{
    padding: 0px;
    margin: 0px;
    /* font-size: 14px;
    line-height: 14px; */
    font-family: Arial, 'Hiragino Sans GB', 'Microsoft Yahei', Tahoma, Helvetica, STHeiti;
}
a{
    color: black!important;
    text-decoration: none!important;
}
a:checked{
    text-decoration: none!important;
}
a:visited{
    text-decoration: none!important;
}
a:hover{
    text-decoration: none!important;
}
body{
    background-color: #F3F3F3;
}

.masterShow{
    width: 100%;
    height: 80px;
    background-color: #fff;
}

.masterShow .mS_header{
    width: 50px;
    height: 50px;
    border-radius: 5px;
}
.masterShow .mS_info{
    display: inline-block;
    padding-left: 10px;
    margin-top: 10px;
}
.masterShow .mS_info p{
    margin: 1px;
}
.masterShow .mS_info .mC_Des span{
    display: inline-block;
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
}
.masterShow .mS_info .mC_Des span:nth-of-type(1){
    width: 60px;
}
.masterShow .mS_info .mC_Des span:nth-of-type(2){
    width: 60px;
}
.masterShow .mS_info .mC_Des span:nth-of-type(3){
    width: 30px;
}
.masterShow .mS_headerBorder{
    display: inline-block;
    border-radius: 2px;
    margin-left: 10px;
    margin-top: 10px;

}
      
.mS_info .mS_masterName{
    font-weight: bold;
}

.line{
    /*background: url(../i/show_master_card_footer_hb.png);*/
    width: 100%;
    height: 2px;
    background-size: contain;
    margin-top: 3px;
}
    
.albumCard{
    width: 100%;
    border-radius: 5px;
    margin-top: 10px;
}
.albumCard .aC_head{
    background: #A2D016;
    color: white;
    padding: 0px 10px;
    font-size: 16px;
}
.albumCard .aC_head mip-img{
    width: 12px;
    height: 12px;
}
.albumCard .aC_head span mip-img{
    width: 8px;
    height: 14px;
    margin-top: -3px;
}
.albumCard .aC_head span{
    line-height: 30px;
}
.albumCard .aC_head span:nth-of-type(2){
    position: absolute;
    right: 15px;
}
.albumCard .picList{
    overflow: auto;
    white-space: nowrap;
    padding: 10px;
    background-color: white;
    border-radius: 0 0 5px 5px;
}
.albumCard .picList p:first-child{
  margin: 0;
}
.albumCard .picList mip-img{
    height: 70px;
    width: 70px;
    cursor: pointer;
    display: inline-block;
    margin-right: 10px;
    border-radius: 5px;
}

.serverCard{
    width: 100%;
    border-radius: 5px;
    margin-top: 10px;
}
.serverCard tbody tr{
  border-bottom: 1px solid #eee;
}
.serverCard tbody tr td:nth-of-type(1){
  height:49px;
}
.serverCard tbody tr td:nth-of-type(2){
  border-left: 1px solid #eee;
  border-right: 1px solid #eee;
}
.serverCard .sC_head{
    height: 30px;
    color: #fff;
    line-height: 30px;
    font-size: 16px;
    cursor: pointer;
    background: #F16B57;
    background-color:#33CC99;
    padding: 0px 10px;
}
.serverCard .sC_head mip-img{
    width: 12px;
    height: 12px;
}
.serverCard .sC_head span mip-img{
    width: 8px;
    height: 14px;
    margin-top: -3px;
}
.serverCard .sC_head span{
    line-height: 30px;
}
.serverCard .sC_head span:nth-of-type(2){
    position: absolute;
    right: 15px;
}
.serverCard table{
    width: 100%;
    background-color: white;
    text-align: center;
}
.serverCard .price{
    width: 100%;
    background-color: white;
    border-radius: 0 0 5px 5px;
}
.serverCard .price p{
    line-height: 40px;
    text-align: center;
    margin: 0px;
}
.serverCard .price p span:nth-of-type(1){
    text-decoration:line-through;
    color: #C32218;
}
.serverCard .price p span:nth-of-type(2){
    padding-left:10%;
}
.serverCard .price p span:nth-of-type(3){
    color: #C32218;
}

.pingJiaCard{
    width: 100%;
    border-radius: 5px;
    margin-top: 10px;
    background-color: #fff;
    padding-top: 10px;
    padding-bottom: 50px;
}
.pingJiaCard .pJC_head{
    height: 30px;
    color: #fff;
    line-height: 30px;
    font-size: 16px;
    cursor: pointer;
    background: #6BD4FA;
    padding: 0px 10px;
}
.pingJiaCard .pJC_head mip-img{
    width: 12px;
    height: 12px;
}
.pingJiaCard .pJC_head span mip-img{
    width: 8px;
    height: 14px;
    margin-top: -3px;
}
.pingJiaCard .pJC_head span{
    line-height: 30px;
}
.pingJiaCard .pJC_head span:nth-of-type(2){
    position: absolute;
    right: 15px;
}
.pingJiaCard .pingJia{
    background-color: white;
    border-radius: 0 0 5px 5px;
}
.pingjiacard .pingjia p:first-child{
  padding:10px 0px 10px 10px;
}
.pingjiacard .pingjia tbody tr:first-child{
  padding:10px 0px 10px 10px;
}
.pingjiacard .pingjia tbody tr:nth-of-type(1) td,
.pingjiacard .pingjia tbody tr:nth-of-type(2) td,
{
  line-height:30px;
  border-bottom: 1px solid #eee;
}
.pingjiacard .pingjia tbody tr:nth-of-type(3) .customerInfo p:nth-of-type(1){
  font-size:15px;line-height: 16px;
}
.pingjiacard .pingjia tbody tr:nth-of-type(3) .customerInfo p:nth-of-type(2){
  color: #999;
}
.pingjiacard .pingjia tbody tr:nth-of-type(4) td{
  line-height:30px;border-bottom: 1px solid #eee;
}
.pingJiaCard table{
    width: 100%;
    border-radius: 0 0 5px 5px;
}
.pingJiaCard table td{
    padding: 0 10px;
}
.pingJiaCard .starBox{
    width: 90px;
    height: 16px;
    display: inline-block;
    position: absolute;
    right:15px;
}
.pingJiaCard .starBox mip-img{
    width: 12px;
    height: 12px;
}
.pingJiaCard .left{
    float: right;
}
.pingJiaCard .customer{
    padding: 10px;
    border-bottom: 1px solid #eee;
}
.pingJiaCard .customer mip-img{
    height: 50px;
    width: 50px;
    display: inline-block;
    margin-right: 10px;
    border-radius: 5px;
}
.pingJiaCard .customer .customerInfo{
    display: inline-block;
    vertical-align: top;
    width: 75%;
}
.pingJiaCard .customer .customerInfo p:last-child{
    margin-top: 0px;
}
.pingJiaCard .customerEvaluate{
    padding: 10px;
    border-bottom: 1px solid #eee;
    border-radius: 0 0 5px 5px;
}
.pingJiaCard .cE_title{
    font-size: 16px;
    margin: 0px;
}
.pingJiaCard .cE_article{
    line-height: 1.3;
}
.pingJiaCard .customerEvaluate mip-img{
    height: 50px;
    width: 50px;
    display: inline-block;
    margin-right: 10px;
    border-radius: 5px;
}

.jieshao{
    background-color: white;
    /*padding: 10px;*/
    padding-bottom: 1px;
    margin-top: 10px;
}

.jieshao .pJC_head{
    height: 30px;
    color: #fff;
    line-height: 30px;
    font-size: 16px;
    cursor: pointer;
    background: #6BD4FA;
    padding: 0px 10px;
    margin-bottom: 10px;
}

td.firstCol {
    width:80px;
    text-align:right;
    vertical-align:top;
    padding-top:28px;
    padding-right:10px;
}

td.secondCol {
    vertical-align:top;
    padding-top:25px;
    text-align:left;
}

.tbl{
    width:100%;
    text-align: center;
    height: 50px;
    border-top: 1px solid #ddd;
    position: fixed;
    bottom: 0;
    background-color: #fff;
}
.tbl td{
    border-right:1px solid #ddd;
}
.td1{
    cursor: pointer;
    background-color: #fff;
}
.td-fav{
  padding-left:10px;
  padding-right: 10px;
}
.td2{
    cursor: pointer;
    background-color: #adcd41;
}
.td2 a{
    color:white !important;
}
.td1 .a{
    display:block;
    /*width:25px;*/
    /*height:25px;*/
    margin:0 auto;
}

.fav_p{
    font-size: 10px;
    margin:0;
    margin-top: 4px;
    line-height:10px;
}
.fav{
    display:block;
    width:20px;
    margin:0 auto;
    vertical-align: middle; 
}
    
.fuwu{
    /*width: 95%;*/
    height: 70px;
    background-color: #fff;
    margin-top: 10px;
    padding-left: 10px;
    padding-top: 1px;
}

.expectCity{
    margin-top: 10px;
}

.red{
    color: red;
}

.more_less{
    text-align: center;
}

.mip-showmore-btn{
    text-align: center;
    display: inline-block;
    width: 100%;
    padding: 0px;
    border:none;
    background-color: white !important;
    margin-top: 5px;
}

.jieshao_content{
    margin-left: 10px;
    margin-right: 10px;
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
  //console.log(ret);
    if(ret.success) cb(true, ret.data);
    else cb(false, ret.error);
  })  
  .catch(e => {
    console.error(e.message); 
    cb(false, e.message);
  });
}


API.getMasterInfo = function(masterId, cb) {
  API.wrapRet_(
    '/api/get_master_info_for_me', 
    {
      'master_id': masterId
    },
    cb);
};

API.favMaster = function(masterId, cb) {
  API.wrapRet_(
    '/api/fav_master', 
    {
      'master_id': masterId
    },
    cb);
}


API.unfavMaster = function(masterId, cb) {
  API.wrapRet_(
    '/api/unfav_master', 
    {
      'master_id': masterId
    },cb);
}

export default {
  mounted () {
    console.log('This is master card component !')
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
    return {
      data: pdata.data,
      isLogin:pdata.isLogin,
      isUnion:pdata.isUnion
    }
  },
  computed: {
    
  },
  methods: {
    init () {
      console.log('should loading');
      console.log(this.dataJson);
      this.reload_();
    },
  created() {

      this.reload_();
  },

  checkLogin_() {
    if(!this.isLogin){
        window.location.href = '/do_login?to=' + encodeURIComponent(window.location.href);
           return;
    }
    return true;
  },

  reload_() {
    console.log('reloading');

    var self = this;
    API.getMasterInfo(this.data.info.id, function(isOk, data){
      if (isOk) {
        self.$set(self.data.info, 'isfav', data.fav);
        self.$set(self.data.info, 'can_online_interview', data.can_online_interview);
        self.$set(self.data.info, 'order_desc_str', data.order_desc_str);
        //console.log(self);
      } else {
        console.warn(data);
      }
    });

  },
  handleFav(){
    console.log('handleFav');
    if(!this.checkLogin_()) return;
    
    if(this.data.info.isfav) {
      this.$set(this.data.info,'isfav',false);
    console.log(this.data.info);
      console.log('unFav');
      API.unfavMaster(this.data.info.id, this.reload_);
    } else {
      this.$set(this.data.info,'isfav',true);
    console.log(this.data.info);
      console.log('Fav');
      API.favMaster(this.data.info.id, this.reload_);
    }
  },
  load_data () {
      console.log('should set data');
    }
  }

}
</script>
