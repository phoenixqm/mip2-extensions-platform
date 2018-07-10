<template>
<div class="root">


<table class="sousuo_table">
  <tbody><tr>
    <td class="ss_city_td">
        
      <span on="tap:my-lightbox2.toggle" id="btn-open" class="city_btn" role="button" tabindex="0">北京</span>
      
    </td>
    <td class="sousuo_td">
      <input type="text" name="kw" class="kw" validatetarget="kw" placeholder="输入月嫂的姓名搜索">
      <mip-img class="sousuo_icon mip-element mip-layout-container mip-img-loaded" src="/i/sousuo.png"><img class="mip-fill-content mip-replaced-content" src="/i/sousuo.png"></mip-img>
    
    <input class="sousuo" type="submit" value="搜索">
    <a class="person" href="/order_list"><mip-img width="28px" height="23px" src="/i/select_per.png" class="mip-element mip-layout-fixed mip-layout-size-defined mip-img-loaded" style="width: 28px; height: 23px;"><img class="mip-fill-content mip-replaced-content" src="/i/select_per.png"></mip-img></a></td>
  </tr>
</tbody></table>
<mip-lightbox id="my-lightbox2" layout="nodisplay" class="mip-layout-nodisplay mip-element" content-scroll="" style="display: none; position: fixed; z-index: 10001; top: 0px; right: 0px; left: 0px; transition: opacity 0.1s ease-in;">
    
  <div class="mip-fill-content"><div class="lightbox">
      <table class="city_title"><tbody><tr><td>已开通服务的城市：</td></tr></tbody></table>
      <table id="citybar" class="citybar" data-city="">

        <tbody><tr>
          <td class="citytd">北京</td>
          <td class="citytd">天津</td>
          <td class="citytd">哈尔滨</td>
          <td class="citytd">武汉</td>
        </tr>
        <tr>
          <td class="citytd">上海</td>
          <td class="citytd">长春</td>
          <td class="citytd">济南</td>
          <td class="citytd">长沙</td>
        </tr>
        <tr>
          <td class="citytd">广州</td>
          <td class="citytd">杭州</td>
          <td class="citytd">洛阳</td>
          <td class="citytd">南阳</td>
        </tr>
        <tr>
          <td class="citytd">深圳</td>
          <td class="citytd">沈阳</td>
          <td class="citytd">石家庄</td>
          <td class="citytd">西安</td>
        </tr>
        <tr>
          <td class="citytd">湘潭</td>
          <td class="citytd">徐州</td>
          <td class="citytd">成都</td>
          <td class="citytd">南京</td>
        </tr>
        <tr>
          <td class="citytd">黄石</td>
          <td class="citytd">郑州</td>
          <td class="citytd">青岛</td>
          <td class="citytd">大连</td>
        </tr>
        <tr>
          <td class="citytd">常州</td>
          <td class="citytd">唐山</td>
          <td class="citytd">保定</td>
          <td class="citytd">秦皇岛</td>
        </tr>
        <tr>
          <td class="citytd">呼和浩特</td>
          <td class="citytd">乌鲁木齐</td>
          <td class="citytd">合肥</td>
          <td class="citytd">南昌</td>
        </tr>
        <tr>
          <td class="citytd">福州</td>
          <td class="citytd">厦门</td>
          <td class="citytd">香港</td>
          <td class="citytd">南宁</td>
        </tr>       
      </tbody></table>
        <span class="lightbox-close" id="lightbox-close">确认</span>
    </div></div></mip-lightbox>

<table id="sortbar" class="sort_by" data-sort_by="">
    <tbody><tr>
      <td id="sortZH" class="checked">综合
        
        <mip-img src="/i/select_master_jt_down_white.png" class="mip-element mip-layout-container mip-img-loaded"><img class="mip-fill-content mip-replaced-content" src="/i/select_master_jt_down_white.png"></mip-img>
        
      </td>
      <td id="sortPrice">按价格
        
        <mip-img src="/i/select_master_jt_down.png" class="mip-element mip-layout-container mip-img-loaded"><img class="mip-fill-content mip-replaced-content" src="/i/select_master_jt_down.png"></mip-img>
        
      </td>
      <td id="sortJY">按经验
        
        <mip-img src="/i/select_master_jt_down.png" class="mip-element mip-layout-container mip-img-loaded"><img class="mip-fill-content mip-replaced-content" src="/i/select_master_jt_down.png"></mip-img>
        
      </td>
      <td id="sortAge">按年龄
        
        <mip-img src="/i/select_master_jt_up.png" class="mip-element mip-layout-container mip-img-loaded"><img class="mip-fill-content mip-replaced-content" src="/i/select_master_jt_up.png"></mip-img>
        
      </td>
      <td class="shaixuan_btn" on="tap:right-sidebar.open">筛选
        <mip-img src="/i/select_master_jt_down.png" class="mip-element mip-layout-container mip-img-loaded"><img class="mip-fill-content mip-replaced-content" src="/i/select_master_jt_down.png"></mip-img>
      </td>
    </tr>
  </tbody>
</table>



<div class="innerroot">

    <div class="rec_a">
      <a href="/update_ycq_mip" >
        <mip-img class="rec_icon" layout="fixed" width="78px" height="50px" src='i/bwtj.png' ></mip-img>
      </a>
    </div>
  
    <mip-form method="get" url="https://mip.putibaby.com/select_master" name="mip-form" class="  mip_form mip-element mip-layout-container">  

      <table class="yssxtj_table">
        <tbody><tr><td class="yssxtj">月嫂筛选条件</td></tr>
      </tbody></table>
      <table class="hidden-table hidden-table_top">
        
        <tbody><tr>
          <td>上户类型：</td>
          
            <td class="qt_td"><input type="radio" name="shlxRow" checked="" class="radio_qt" value="全天">全天</td>
            <td class="bb_td"><input type="radio" name="shlxRow" class="radio_bb" value="白班">白班</td>
          

        </tr>
      </tbody></table>
      <table class="hidden-table">
        <tbody><tr>
          <td>预产期：</td>
          <td><input type="date" class="ycq" name="ycq"></td>
        </tr>
        <tr>
          <td>上户城市：</td>
          <td>
            <select name="city" class="city">
              <option value="">不限</option>
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
              
                 <option value="">不限</option>
              
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
      </tbody></table>

      <table class="hidden-table">
        <tbody><tr>
          <td>期望价格：</td>
          <td>
            <select name="priceFromSel" class="priceFromSel">
               <option selected="" value="0">0元</option>
              
                  <option selected="true" value="0">
                    0元
                  </option>
                
                  <option value="1000">
                    1000元
                  </option>
                
                  <option value="2000">
                    2000元
                  </option>
                
                  <option value="3000">
                    3000元
                  </option>
                
                  <option value="4000">
                    4000元
                  </option>
                
                  <option value="5000">
                    5000元
                  </option>
                
                  <option value="6000">
                    6000元
                  </option>
                
                  <option value="7000">
                    7000元
                  </option>
                
                  <option value="8000">
                    8000元
                  </option>
                
                  <option value="9000">
                    9000元
                  </option>
                
                  <option value="10000">
                    10000元
                  </option>
                
                  <option value="11000">
                    11000元
                  </option>
                
                  <option value="12000">
                    12000元
                  </option>
                
                  <option value="13000">
                    13000元
                  </option>
                
                  <option value="14000">
                    14000元
                  </option>
                
                  <option value="15000">
                    15000元
                  </option>
                
                  <option value="16000">
                    16000元
                  </option>
                
                  <option value="17000">
                    17000元
                  </option>
                
                  <option value="18000">
                    18000元
                  </option>
                
                  <option value="19000">
                    19000元
                  </option>
                
                  <option value="20000">
                    20000元
                  </option>
                
                  <option value="21000">
                    21000元
                  </option>
                
                  <option value="22000">
                    22000元
                  </option>
                
                  <option value="23000">
                    23000元
                  </option>
                
                  <option value="24000">
                    24000元
                  </option>
                
                  <option value="25000">
                    25000元
                  </option>
                
                  <option value="26000">
                    26000元
                  </option>
                
                  <option value="27000">
                    27000元
                  </option>
                
                  <option value="28000">
                    28000元
                  </option>
                
                  <option value="29000">
                    29000元
                  </option>
                
                  <option value="30000">
                    30000元
                  </option>
                
                  <option value="31000">
                    31000元
                  </option>
                
                  <option value="32000">
                    32000元
                  </option>
                
                  <option value="33000">
                    33000元
                  </option>
                
                  <option value="34000">
                    34000元
                  </option>
                
                  <option value="35000">
                    35000元
                  </option>
                
                  <option value="36000">
                    36000元
                  </option>
                
                  <option value="37000">
                    37000元
                  </option>
                
                  <option value="38000">
                    38000元
                  </option>
                
                  <option value="39000">
                    39000元
                  </option>
                
                  <option value="40000">
                    40000元
                  </option>
                
                  <option value="41000">
                    41000元
                  </option>
                
                  <option value="42000">
                    42000元
                  </option>
                
                  <option value="43000">
                    43000元
                  </option>
                
                  <option value="44000">
                    44000元
                  </option>
                
                  <option value="45000">
                    45000元
                  </option>
                
                  <option value="46000">
                    46000元
                  </option>
                
                  <option value="47000">
                    47000元
                  </option>
                
                  <option value="48000">
                    48000元
                  </option>
                
                  <option value="49000">
                    49000元
                  </option>
                
                  <option value="50000">
                    50000元
                  </option>
                

            </select>
          </td>
          <td><span class="from_to">到</span></td>
          <td>
           <select name="priceToSel" class="priceToSel">
            <option selected="" value="50000">50000元</option>
            
              <option value="0">
                0元
              </option>
            
              <option value="1000">
                1000元
              </option>
            
              <option value="2000">
                2000元
              </option>
            
              <option value="3000">
                3000元
              </option>
            
              <option value="4000">
                4000元
              </option>
            
              <option value="5000">
                5000元
              </option>
            
              <option value="6000">
                6000元
              </option>
            
              <option value="7000">
                7000元
              </option>
            
              <option value="8000">
                8000元
              </option>
            
              <option value="9000">
                9000元
              </option>
            
              <option value="10000">
                10000元
              </option>
            
              <option value="11000">
                11000元
              </option>
            
              <option value="12000">
                12000元
              </option>
            
              <option value="13000">
                13000元
              </option>
            
              <option value="14000">
                14000元
              </option>
            
              <option value="15000">
                15000元
              </option>
            
              <option value="16000">
                16000元
              </option>
            
              <option value="17000">
                17000元
              </option>
            
              <option value="18000">
                18000元
              </option>
            
              <option value="19000">
                19000元
              </option>
            
              <option value="20000">
                20000元
              </option>
            
              <option value="21000">
                21000元
              </option>
            
              <option value="22000">
                22000元
              </option>
            
              <option value="23000">
                23000元
              </option>
            
              <option value="24000">
                24000元
              </option>
            
              <option value="25000">
                25000元
              </option>
            
              <option value="26000">
                26000元
              </option>
            
              <option value="27000">
                27000元
              </option>
            
              <option value="28000">
                28000元
              </option>
            
              <option value="29000">
                29000元
              </option>
            
              <option value="30000">
                30000元
              </option>
            
              <option value="31000">
                31000元
              </option>
            
              <option value="32000">
                32000元
              </option>
            
              <option value="33000">
                33000元
              </option>
            
              <option value="34000">
                34000元
              </option>
            
              <option value="35000">
                35000元
              </option>
            
              <option value="36000">
                36000元
              </option>
            
              <option value="37000">
                37000元
              </option>
            
              <option value="38000">
                38000元
              </option>
            
              <option value="39000">
                39000元
              </option>
            
              <option value="40000">
                40000元
              </option>
            
              <option value="41000">
                41000元
              </option>
            
              <option value="42000">
                42000元
              </option>
            
              <option value="43000">
                43000元
              </option>
            
              <option value="44000">
                44000元
              </option>
            
              <option value="45000">
                45000元
              </option>
            
              <option value="46000">
                46000元
              </option>
            
              <option value="47000">
                47000元
              </option>
            
              <option value="48000">
                48000元
              </option>
            
              <option value="49000">
                49000元
              </option>
            
              <option value="50000">
                50000元
              </option>
            
           </select>
          </td>
        </tr>

        <tr>
          <td>年龄要求:</td>
          <td>
            <select name="ageFromSel" class="ageFromSel">
              <option selected="" value="20">20岁</option>
              
                <option selected="true" value="20">
                  20岁
                </option>
              
                <option value="25">
                  25岁
                </option>
              
                <option value="30">
                  30岁
                </option>
              
                <option value="35">
                  35岁
                </option>
              
                <option value="40">
                  40岁
                </option>
              
                <option value="45">
                  45岁
                </option>
              
                <option value="50">
                  50岁
                </option>
              
                <option value="55">
                  55岁
                </option>
              
            </select>
          </td>
      <td><span class="from_to">到</span></td>
          <td>  
            <select name="ageToSel" class="ageToSel">     
              <option selected="" value="55">55岁</option>
              
                <option value="20">
                  20岁
                </option>
              
                <option value="25">
                  25岁
                </option>
              
                <option value="30">
                  30岁
                </option>
              
                <option value="35">
                  35岁
                </option>
              
                <option value="40">
                  40岁
                </option>
              
                <option value="45">
                  45岁
                </option>
              
                <option value="50">
                  50岁
                </option>
              
                <option value="55">
                  55岁
                </option>
              
            </select>
          </td>
      </tr>

      <tr>
        <td>从业年限:</td>
        <td>
          <select name="workYearFromSel" class="workYearFromSel">
            <option selected="" value="1">1年</option>
            
              <option selected="true" value="1">
                1年
              </option>
            
              <option value="2">
                2年
              </option>
            
              <option value="3">
                3年
              </option>
            
              <option value="4">
                4年
              </option>
            
              <option value="5">
                5年
              </option>
            
              <option value="6">
                6年
              </option>
            
              <option value="7">
                7年
              </option>
            
              <option value="8">
                8年
              </option>
            
              <option value="9">
                9年
              </option>
            
              <option value="10">
                10年
              </option>
            
          </select>
        </td>
        <td><span class="from_to">到</span></td>
        <td>
          <select name="workYearToSel" class="workYearToSel">
            
              <option selected="" value="">不限</option>
            
            
              <option value="1">
                1年
              </option>
            
              <option value="2">
                2年
              </option>
            
              <option value="3">
                3年
              </option>
            
              <option value="4">
                4年
              </option>
            
              <option value="5">
                5年
              </option>
            
              <option value="6">
                6年
              </option>
            
              <option value="7">
                7年
              </option>
            
              <option value="8">
                8年
              </option>
            
              <option value="9">
                9年
              </option>
            
              <option value="10">
                10年
              </option>
            
          </select>
        </td>
      </tr>
      </tbody></table>
      <span class="quxiao" on="tap:right-sidebar.close">取消</span>
      <input class="queding" type="submit" value="确定">
      </mip-sidebar>
  
    </mip-form>
  
    <div class="cardList">
    <div v-for="m in list">
        <div class="masterCard">
          <a :href="'/master_card?id='+m.id">
          <div class="div-padding">
            <mip-img layout="responsive" width="70" height="70"
             class="mC_header" :src="m.header.small" ></mip-img>
            <div class="mC_info">
              <p class="mC_masterName">{{ m.name }}</p>
              <p class="starBox">

                <mip-img v-for="p in m.star_1_list" layout="responsive" width="12" height="12"
                 class="iconStar" src="/i/select_master_star.png" /></mip-img>

                <mip-img v-for="p in m.star_0_list"  layout="responsive" width="12" height="12"
                 class="iconStar" src="/i/select_master_unstar.png" /></mip-img>


              </p>
              <div class="mC_Des">
                <span>
                 <mip-img layout="responsive" width="11" height="11"
                 class="icon" src="/i/age.png" /></mip-img>
                 {{ m.desc_list_0 }}</span>
                <span><mip-img layout="responsive" width="11" height="11"
                 class="icon" src="/i/work_year.png" /></mip-img>
                {{ m.desc_list_2 }}</span>
                <span><mip-img layout="responsive" width="11" height="11"
                 class="icon" src="/i/jiguan.png" /></mip-img>
                 {{ m.desc_list_1 }}</span>
              </div>
              <span class="ptgPrice"><b>￥{{ m.ptg_price }}</b></span>
            </div>
          </div>
          </a>
        </div>
    </div>
    <div class="mip-infinitescroll-results"></div>
    <div class="bg">
        <div class="mip-infinitescroll-loading"></div>
    </div>
  
  
    </div>

</div>

</div>
<style scoped>
.wrapper {
  margin: 0 auto;
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
      console.log(ret);
      if (ret.success) cb(true, ret.data);
      else cb(false, ret.error);
    })
    .catch(e => {
      console.error(e.message);
      cb(false, e.message);
    });
}

API.getSelectMaster = function(filter, cb) {
  API.wrapRet_(
    '/api/get_select_master', {
      'filter': filter
    },
    cb);
};


export default {
  mounted() {
    console.log('This is pty order list component !');
    var self = this;
    this.$element.customElement.addEventAction('echo', function(event, str) {
      console.log(event);
    });
    this.$element.customElement.addEventAction('dook', function(event, str) {
      // console.log(event);

      console.log(event.from);
      event.from.bind(self)(event.data, true);
      //var eval_str = 'this.' + event.handler + '(event_order)'
    });
    this.$element.customElement.addEventAction('docancel', function(event, str) {
      console.log(event);
      console.log(str);

    });

    //修改url中某个指定的参数的值 
    function changeURLArg(url,arg,arg_val){
      var pattern=arg+'=([^&]*)'; 
      var replaceText=arg+'='+arg_val; 
      if(url.match(pattern)){ 
          var tmp='/('+ arg+'=)([^&]*)/gi'; 
          tmp=url.replace(eval(tmp),replaceText); 
          return tmp; 
      }else{ 
          if(url.match('[\?]')){ 
              return url+'&'+replaceText; 
          }else{ 
              return url+'?'+replaceText; 
          } 
      } 

      return url+'\n'+arg+'\n'+arg_val; 
      
    }

    //无历史记录sort_by分类跳转
    function jump(new_sort_by){
      var url = window.location.href;  
      url = changeURLArg(url,'sort_by',new_sort_by);    
      window.location.replace(url); 

    }

    function addClass(element, new_name) {  
      if (!element || !new_name) return false;  
      if (element.className) {  
          var old_class_name = element.className;  
          element.className = old_class_name + " " + new_name;  
      } else{  
          element.className = new_name;  
      }  
      return true;  
    } 

    function removeClass(element, class_name) {  
      if(!element || !class_name) return false;  
      // if (!element.className) return false;
      for (var n = 0; n < element.length; n++) {
         
        var all_names = element[n].className.split(" ");  
        for (var i = 0; i < all_names.length; i++) {  
            if (all_names[i] === class_name) {  
                all_names.splice(i, 1);  
                element[n].className = "";  
                for (var j = 0; j < all_names.length; j++) {  
                    element[n].className += " ";  
                    element[n].className += all_names[j];  
                }  
                return true;  
            }  
        } 
      }    
    }  


    var sortbar = document.querySelector("#sortbar");
    var sort_by = sortbar.dataset.sort_by;
    var sortZH = document.querySelector("#sortZH");
    var sortPrice = document.querySelector("#sortPrice");
    var sortJY = document.querySelector("#sortJY");
    var sortAge = document.querySelector("#sortAge");
    var city = sortbar.dataset.city;
    var lightbox_close= document.querySelector("#lightbox-close");

    if (sort_by == 'price_asc' || sort_by == 'price_desc') {
      addClass(sortPrice,'checked');
    }else if (sort_by == 'jy_asc' || sort_by == 'jy_desc') {
      addClass(sortJY,'checked');
    }else if (sort_by == 'age_asc' || sort_by == 'age_desc') {
      addClass(sortAge,'checked');
    }else{
      addClass(sortZH,'checked');
    }

    sortZH.addEventListener('click', function(){        
      jump(''); 
    });

    sortPrice.addEventListener('click', function(){
      if (sort_by == 'price_desc') {
        jump('price_asc');
      }else{
        jump('price_desc');
      }  
    }); 

    sortJY.addEventListener('click', function(){
      if (sort_by == 'jy_desc') {
        jump('jy_asc');
      }else{
        jump('jy_desc');
      }  
    }); 
    
    sortAge.addEventListener('click', function(){
      if (sort_by == 'age_asc') {
        jump('age_desc');
      }else{
        jump('age_asc');
      }
    }); 

    var citytd = document.querySelectorAll(".citytd");
    var city_val = document.querySelector("#btn-open").innerHTML;
    
    for (var i = 0; i < citytd.length; i++) {
      citytd[i].addEventListener('click',function () {
        removeClass(citytd,'checked');
        addClass(this,'checked');
        city_val = this.innerHTML;
      })
    }
    
    lightbox_close.addEventListener('click',function () {
      var url = window.location.href;  
      url = changeURLArg(url,'city',city_val);
      window.location.replace(url);
    });


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
    console.log(pdata.list);
    return {
      list: [],
      state: {

      },
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

    reload_() {
      window.location.reload();

    },
  
  }


}
</script>
