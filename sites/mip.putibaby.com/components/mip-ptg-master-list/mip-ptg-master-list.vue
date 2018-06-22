
<template>

<div class="root">

  <div class="rec_a">
      <a href="/verify_phone_number_mip" >
        <mip-img class="rec_icon" layout="fixed" width="80px" height="50px" src='i/bwtj.png' ></mip-img>
      </a>
  </div>

<mip-form method="get" url="http://mip.putibaby.com/select_master" name="mip-form" class='mip_form'>

  <span class="click">
    <input  type="text" name="kw" class="kw" validatetarget="kw" placeholder="输入月嫂的姓名搜索">
    <input class="sousuo" type="submit" value="搜索">
    <span class="shaixuan" on="tap:right-sidebar.open">筛选</span>
  </span>
</mip-form>

<div style="clear:left;margin:10px;background:#fff;height:30px;border-radius:5px;box-shadow:0 1px 1px 1px #e7ebd0;overflow:hidden;borer:1px solid #ccc;">
   <table style="width:100%;height:100%;">
      <tbody>
         <tr>
            <td id='orderStar' style="cursor:pointer;text-align:center;background:#AFCA48;color:#fff;"><span>综合排序</span></td>
            <td id='orderPrice' style="cursor:pointer;text-align:center;border-right:1px solid #eee;"><span>按价格</span><img src="/assets/i/select_master_jt_down.png" style="width:10px;position:relative;top:-3px;display:inline-block;margin-left:5px;"1.1"></td>
            <td id='orderYears' style="cursor:pointer;text-align:center;border-right:1px solid #eee;"><span>按经验</span><img src="/assets/i/select_master_jt_down.png" style="width:10px;position:relative;top:-3px;display:inline-block;margin-left:5px;"></td>
            <td id='orderAge' style="cursor:pointer;text-align:center;"><span>按年龄</span><img src="/assets/i/select_master_jt_up.png" style="width:10px;position:relative;top:-3px;display:inline-block;margin-left:5px;"></td>
         </tr>
      </tbody>
   </table>
</div>

<mip-form method="get" url="http://mip.putibaby.com/select_master" name="mip-form" class='mip_form'>  

  <mip-sidebar id="right-sidebar" layout="nodisplay" side="right" class="mip-hidden">


    <table class="hidden-table">
      <tr>
        <td>上户城市：</td>
        <td>
          <select name="city" class="city">
            <%if(data.city == ''){%>
               <option value="">不限</option>
            <%}else{%>
               <option value="<%=data.city%>"><%=data.city%></option>
            <%}%>
            <option value="北京">北京</option>
            <option value="天津">天津</option>
            <option value="哈尔滨">哈尔滨</option>
            <option value="武汉">武汉</option>
            <option value="上海">上海</option>
            <option value="长春">长春</option>
            <option value="济南">济南</option>
            <option value="长沙">长沙</option>
            <option value="广州">广州</option>
            <option value="杭州">杭州</option>
            <option value="洛阳">洛阳</option>
            <option value="南阳">南阳</option>
            <option value="深圳">深圳</option>
            <option value="沈阳">沈阳</option>
            <option value="石家庄">石家庄</option>
            <option value="西安">西安</option>
            <option value="湘潭">湘潭</option>
            <option value="徐州">徐州</option>
            <option value="成都">成都</option>
            <option value="南京">南京</option>
            <option value="黄石">黄石</option>
            <option value="郑州">郑州</option>
            <option value="青岛">青岛</option>
            <option value="大连">大连</option>
            <option value="常州">常州</option>
            <option value="唐山">唐山</option>
            <option value="保定">保定</option>
            <option value="秦皇岛">秦皇岛</option>
            <option value="襄阳">襄阳</option>
            <option value="太原">太原</option>
            <option value="昆明">昆明</option>
            <option value="兰州">兰州</option>
            <option value="呼和浩特">呼和浩特</option>
            <option value="乌鲁木齐">乌鲁木齐</option>
            <option value="合肥">合肥</option>
            <option value="南昌">南昌</option>
            <option value="福州">福州</option>
            <option value="厦门">厦门</option>
            <option value="香港">香港</option>
            <option value="南宁">南宁</option>
          </select>
        </td>
      </tr>
      <tr>
        <td>月嫂籍贯：</td>
        <td>
          <select name="jiguan" class="jiguan">
            <%if(data.jiguan == ''){%>
               <option value="">不限</option>
            <%}else{%>
               <option value="<%=data.jiguan%>"><%=data.jiguan%></option>
            <%}%>
            <option value="北京">北京</option>
            <option value="天津">天津</option>
            <option value="上海">上海</option>
            <option value="重庆">重庆</option>
            <option value="新疆">新疆</option>
            <option value="内蒙古">内蒙古</option>
            <option value="黑龙江">黑龙江</option>
            <option value="西藏">西藏</option>
            <option value="青海">青海</option>
            <option value="甘肃">甘肃</option>
            <option value="宁夏">宁夏</option>
            <option value="山西">山西</option>
            <option value="陕西">陕西</option>
            <option value="河北">河北</option>
            <option value="辽宁">辽宁</option>
            <option value="吉林">吉林</option>
            <option value="山东">山东</option>
            <option value="河南">河南</option>
            <option value="湖北">湖北</option>
            <option value="四川">四川</option>
            <option value="贵州">贵州</option>
            <option value="云南">云南</option>
            <option value="广西">广西</option>
            <option value="广东">广东</option>
            <option value="福建">福建</option>
            <option value="湖南">湖南</option>
            <option value="江西">江西</option>
            <option value="浙江">浙江</option>
            <option value="江苏">江苏</option>
            <option value="海南">海南</option>
            <option value="安徽">安徽</option>
          </select>
        </td>
      </tr>
    </table>

    <table class="hidden-table">
      <tr>
        <td>期望价格：</td>
        <td>
          <select name="priceFromSel" class="priceFromSel">
             <option selected="" value="<%=data.priceFromSel%>"><%=data.priceFromSel%>元</option>
            <% for(var j=0; j<=50000; j+=1000) {%>
                <option
                <%if(j==0){%>selected="true"<%}%>
                value="<%= j %>">
                  <%= j %>元
                </option>
              <%}%>

          </select>
        </td>
        <td><span class="from_to">--</span></td>
        <td>
         <select name="priceToSel" class="priceToSel">
          <option selected="" value="<%=data.priceToSel%>"><%=data.priceToSel%>元</option>
          <% for(var j=0; j<=50000; j+=1000) {%>
            <option value="<%= j %>">
              <%= j %>元
            </option>
          <%}%>
         </select>
        </td>
      </tr>

      <tr>
        <td>年龄要求:</td>
        <td>
          <select name="ageFromSel" class="ageFromSel">
            <option selected="" value="<%=data.ageFromSel%>"><%=data.ageFromSel%>岁</option>
            <% for(var j=20; j<=55; j+=5) {%>
              <option
                <%if(j==20){%>selected="true"<%}%>
              value="<%= j %>">
                <%= j %>岁
              </option>
            <%}%>
          </select>
        </td>
        <td>--</td>
        <td>  
          <select name="ageToSel" class="ageToSel">     
            <option selected="" value="<%=data.ageToSel%>"><%=data.ageToSel%>岁</option>
            <% for(var j=20; j<=55; j+=5) {%>
              <option value="<%= j %>">
                <%= j %>岁
              </option>
            <%}%>
          </select>
        </td>
    </tr>

    <tr>
      <td>从业年限:</td>
      <td>
        <select name="workYearFromSel" class="workYearFromSel">
          <option selected="" value="<%=data.workYearFromSel%>"><%=data.workYearFromSel%>年</option>
          <% for(var j=1; j<=10; j+=1) {%>
            <option
              <%if(j==1){%>selected="true"<%}%>
            value="<%= j %>">
              <%= j %>年
            </option>
          <%}%>
        </select>
      </td>
      <td><span class="from_to">--</span></td>
      <td>
        <select name="workYearToSel" class="workYearToSel">
          <%if(data.workYearToSel == ''){%>
            <option selected="" value="">不限</option>
          <%}else{%>
            <option selected="" value="<%=data.workYearToSel%>"><%=data.workYearToSel%>年</option>
          <%}%>
          <% for(var j=1; j<=10; j+=1) {%>
            <option value="<%= j %>">
              <%= j %>年
            </option>
          <%}%>
        </select>
      </td>
    </tr>
    </table>
    <input class="queding" type="submit" value="确定">
  </mip-sidebar>
</mip-form>

<mip-infinitescroll data-src="<%= data.url %>" template="myTemplate">

   <script type="application/json">
        {
        "rn": 2000,
        "pn": 0,
        "prn": 10,
        "pnName": "pn",
        "bufferHeightPx": 40,
        "timeout": 5000,
        "loadingHtml": "更多数据正在路上",
        "loadFailHtml": "数据加载失败啦",
        "loadOverHtml": "没有数据了哦"
        }
    </script>
  <div class="cardList">
    <template type="mip-mustache"  id="myTemplate">



        <div class="masterCard">
          <a href="/master_card?id={{id}}">
          <div class="div-padding">
            <mip-img layout="responsive" width="50" height="50"
             class="mC_header" src="{{header.small}}" ></mip-img>
            <div class="mC_info">
              <p class="mC_masterName">{{name}}</p>
              <p class="starBox">
                {{#star_1_list}}
                <mip-img  layout="responsive" width="12" height="12"
                 class="iconStar" src="/i/select_master_star.png" /></mip-img>
                {{/star_1_list}}

                {{#star_0_list}}
                <mip-img layout="responsive" width="12" height="12"
                 class="iconStar" src="/i/select_master_unstar.png" /></mip-img>
                {{/star_0_list}}

              </p>
              <div class="mC_Des">
                <mip-img layout="responsive" width="11" height="11"
                 class="icon" src="/i/select_master_age.png" /></mip-img>
                <span>{{desc_list_0}}</span>
                <mip-img layout="responsive" width="11" height="11"
                 class="icon" src="/i/select_master_work_year.png" /></mip-img>
                <span>{{desc_list_2}}</span>
                <mip-img layout="responsive" width="11" height="11"
                 class="icon" src="/i/select_master_location.png" /></mip-img>
                <span>{{desc_list_1}}</span>
              </div>
              <div class="zhengShu">{{zhengshuStr}}
              </div>
            </div>
          </div>
          <div class="mC_price">
            <div class="line"></div>
            <span class="priceTip">市场价格</span>
            <span class="marketPrice">￥ {{market_price}}</span>
            <span class="priceTip priceRight">菩提果价格<span class="ptgPrice">￥{{ptg_price}}</span></span>
          </div>
          </a>
        </div>
    </template>
    <div class="mip-infinitescroll-results"></div>
    <div class="bg">
        <div class="mip-infinitescroll-loading"></div>
    </div>
  <div class="cardList">
</mip-infinitescroll>
<script src="https://c.mipcdn.com/static/v1/mip-bind/mip-bind.js"></script>
<script src="https://c.mipcdn.com/static/v1/mip-mustache/mip-mustache.js"></script>
<script src="https://c.mipcdn.com/static/v1/mip-form/mip-form.js"></script>
<script src="https://c.mipcdn.com/static/v1/mip-sidebar/mip-sidebar.js"></script>
<script src="https://c.mipcdn.com/static/v1/mip-infinitescroll/mip-infinitescroll.js"></script>
    </div>
</template>


<style scoped>
.wrapper {
  margin: 0 auto;
  text-align: center;
}

.header {
  height: 50px;
  vertical-align: middle;
  padding-left: 10px;
  background-color: rgba(255, 253, 252, 0.9);
}
.header .inner a{
  width: 32%;
}
.header .logo {
  height: 22px;
  width: 85px;
  display: inline-block;
  vertical-align: middle;
  margin-top: 13px;
}
.header .links {
  width: 68%;
  display: inline-block;
  vertical-align: top;
  margin-top: 5px;
}
.header .links td {
  width: 77px;
  /*padding-left: 10%;*/
  text-align: center;
}
.header .links td mip-img{
  height: 34px;
  width: 39.5px;
}
.header .links .yuesao mip-img{
  width: 29.5px;
}
.no{
  display: none;
}
.has{
  display: inline-block;
}

mip-img.head_image {
  height: 50px;
  width: 50px;
  position: absolute;
  left: 10px;
  top: 20px;
  border-radius: 5px;
  border: 0;
}
.div-padding {
  padding: 20px 10px 0px 10px;
}
*{
  padding: 0px;
  margin: 0px;
  font-family: Arial, 'Hiragino Sans GB', 'Microsoft Yahei', Tahoma, Helvetica;
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
  background-color: rgb(245, 245, 229)!important;
  overflow:-Scroll;
  overflow-x:hidden;
}

.root{
  padding: 2% 2.5%;
}
.cardList .masterCard{
  width: 100%;
  height: 140px;
  margin: 10px 0;
  border-radius: 8px;
  box-shadow: 0 1px 1px 1px #e7ebd0;
  background-color: white;
  position: relative;
}
.cardList .masterCard .mC_header{
  width: 50px;
  height: 50px;
  border-radius: 5px;
}
.cardList .masterCard .mC_info{
  display: inline-block;
  vertical-align: top;
  padding-left: 6px;
  width:80%;
  margin-top: -49px;
}
.cardList .masterCard .mC_info .mC_masterName{
  font-size: 16px;
  color:#333;
  display: inline-block;
  margin: -5px 69px;
}
.cardList .masterCard .mC_info .starBox{
  width: 90px;
  height: 16px;
  position: absolute;
  right:8px;
  margin-top: -16px;
}
.cardList .masterCard .mC_info .starBox mip-img{
  width: 12px;
  height: 12px;
  display: inline-block;
}
.cardList .masterCard .mC_info .mC_Des{
  width: 100%;
  line-height: 1;
  margin-top: 10px;
  margin-left: 70px;
}
.cardList .masterCard .mC_info .mC_Des mip-img{
  display: inline-block;
}
.cardList .masterCard .mC_info .mC_Des span{
  color: #999;
  display: inline-block;
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
}
.cardList .masterCard .mC_info .mC_Des span:nth-of-type(1){
  width: 30px;
}
.cardList .masterCard .mC_info .mC_Des span:nth-of-type(2){
  width: 60px;
}
.cardList .masterCard .mC_info .mC_Des span:nth-of-type(3){
  width: 60px;
}
.cardList .masterCard .mC_info .mC_Des .icon{
  width: 11px;
  height: 11px;
  margin-top: -4px;
}
.cardList .masterCard .mC_info .zhengShu{
  color: #666;
  font-size: 12px;
  line-height: 2;
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
  width: 90%;
  margin-left: 70px;
}
.cardList .masterCard .mC_price{
  width: 100%;
  height: 35px;
  background-color: #c2e64e;
  bottom: 0px;
  border-bottom-left-radius:8px;
  border-bottom-right-radius:8px;
  font-size: 16px;
  position: absolute;
}
.cardList .masterCard .mC_price .line{
  background-image: url(../i/select_master_card_huanbian.png);
  background-size: contain;
  height: 4px;
  width: 100%;
  margin-top:0px;
}
.cardList .masterCard .mC_price .priceTip{
  color: white;
  font-size: 14px;
  line-height: 2.5;
  margin-left: 10px;
}
.cardList .masterCard .mC_price .marketPrice{
  text-decoration:line-through;
  color: red;
}
.cardList .masterCard .mC_price .ptgPrice{
  font-size: 16px;
  color: red;
}
.cardList .masterCard .mC_price .priceRight{
  float: right;
  margin-right: 10px;
  line-height: 32px;
}

.line{
  background: url(../i/show_master_card_footer_hb.png);
  width: 100%;
  height: 2px;
  background-size: contain;
  margin-top: 3px;
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

.shlxRow{
  min-height: 90px;
}

.kw{
  float: left;
  width: 180px;
  height: 30px;
  border: 0px solid white;
  font-size: 14px !important;
  padding:1px 5px;
}
.sousuo{
  float: left;
  margin-left: 10px;
  height: 32px;
  background-color: #F5F5E5 !important;
  font-size: 14px !important;
  border: solid 1px #ddd !important;
  display: inline-block !important;
  text-align: center;
  border-radius: 5px;
}

.click{
  /*clear: both;*/
  display: inline-block;
}
.hidden-table tr td {
  height: 45px;
  font-size:10px;
}

.shaixuan{
  width: 40px;
  height: 30px;
  display: inline-block;
  line-height: 32px;
  text-align: center;
  border: solid 1px #ddd;
  border-radius: 5px;
  margin-left: 5px;
  font-size: 14px;
}

.priceFromSel{
  width: 70px;
}

.priceToSel{
  width: 83px;
}

#right-sidebar{
  width: 300px;
  padding-left: 10px;
}

.queding{
  margin-left: 100px;
  margin-top: 30px;
}

.root .rec_a {
  display: block;
  position: fixed;
  right: 0px;
  bottom: 60px;
  width: 80px;
  height: 50px;
  z-index: 99999;
}
.root .rec_a .mip-layout-fixed {
  display: inline-block;
  position: fixed;
  bottom: 60px;
  right: 6px;
}

.root .rec_a .rec_icon: {
  position: fixed;
  display: inline-block;
  width: 80px;
  height: 50px;
}

</style>

<script>
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
    return {
		  list: pdata.list,
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

    }
  }


}
</script>
