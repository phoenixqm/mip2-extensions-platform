
<template>
  <div class='root'>
    <mip-form class="root" method="get" url="https://www.mipengine.org?we=123">

    <div class="yifang">
      <mip-img layout="responsive" width="65" height="65" class="mama_header" src="../i/checked.png"></mip-img>
      <div class="">
        <div class="mama_name" >乙方
          <span class="mama_info_span" >{{ master.name }}</span>
        </div>
        <div class="mama_phone" >电话
          <span class="mama_info_span" >
            <a  href='tel:400-618-8835'>{{ master.phone_number }}</a>
          </span>
        </div>
        <div class="mama_id_card" >身份证
          <span class="mama_info_span" >{{ master.id_card }}
          </span>
        </div>
      </div>
    </div>

    <div class="bingfang">
      <mip-img layout="responsive" width="65" height="65" class="mama_header" src="../i/logo.png"></mip-img>
      <div class="mama_name_b" >丙方
        <span class="mama_info_span" >天津菩提果科技有限公司</span>
      </div>
      <div class="mama_phone_b" >电话
        <span class="mama_info_span" >
          <a  href='tel:400-618-8835'>400-618-8835</a>
        </span>
      </div>
    </div>

      <div class="jiafang" >
        <div class="sub_head" >甲方（我的）信息</div>
        <div class="row" >
          <div class="left" >真实姓名</div>
          <div class="right" >
            <input class="input" v-model="contract_mama_name" type="text" name="username" validatetarget="username" validatetype="must" placeholder="中文姓名">
            <div target="username">姓名不符合规范</div>
          </div>
        </div>
        <div class="row" >
          <div class="left" >手机号</div>
          <div class="right" >
            <input class="input" v-model="contract_mama_phone_number" type="number" name="phone_number" validatetarget="phone_number" validatetype="must" placeholder="手机号码">
            <div target="phone_number">手机号码错误</div>
          </div>
        </div>
        <div class="row" > 
          <div class="left" >身份证号</div>
          <div class="right" >
            <input class="input" v-model="contract_mama_id_card" type="number" name="identity" validatetarget="identity" validatetype="must" placeholder="身份证号码">
            <div target="identity">身份证号码错误</div>
          </div>
        </div>

		<div class="row_photo"  >
          <div>
            <input id="f" type="file" name="f" v-on:change="change" display="none"/>

           	<mip-img class="id_photo"  src="i/vvv.png" ></mip-img>
			
            <span>身份证正面</span>
    			<p>
					<mip-img class="id_photo" layout="responsive" width="185" height="110" id="preview" alt="" name="pic"></mip-img>
				</p>
          </div>
        </div>

        <div class="row_photo"  >
		  <div>
           	<mip-img class="id_photo"  src="i/vvv.png" ></mip-img>
            <span>身份证正面</span>
          </div>
            <!-- <mip-img class="mama_info" src="i/vvv.png" alt="请上传照片" ></mip-img> -->
        </div>

        <div class="row_photo"  >
          <div>
            <mip-img class="id_photo"  src="i/vvv.png" ></mip-img>
            <span>身份证反面</span>
          </div>
          <!-- <mip-img class="mama_info" src="i/vvv.png" alt="请上传照片" ></mip-img> -->
        </div>
      </div>

      <div class="shanghu_info">
        <div class="sub_head" >上户信息</div>
        <div class="row" >
          <div class="left" >服务时间</div>
          <div class="right" >
            <div class="quantian">
              <input type="radio" name="service_time" value="quantian" v-model="contract_is_offer_allday_service"> 全天</input>
            </div>
            <div class="baiban">
              <input type="radio" name="service_time" value="baiban" v-model="contract_is_offer_allday_service"> 白班</input>
            </div>
          </div>
        </div>
        <div class="row" >
          <div class="left" >上户日期</div>
          <div class="right" >
            <input class="input_date" v-model="contract_shanghu_at" type='date' value='' placeholder='请选择月份/年份'/>
          </div>
        </div>
        <div class="row" >
          <div class="left" >上户时长</div>
          <div class="right" >
            <input class="input_sc" v-model="contract_shanghu_length" type='number' value='' />天
          </div>
        </div>
        <div class="row" >
          <div class="left" >26天薪资</div>
          <div class="right" >
			<input class="inputReadOnly" type='number' value='' readOnly="readOnly" />{{contract_master_price}} 元
          </div>
        </div>
        <div class="row" >
          <div class="left" >总金额</div>
          <div class="right" >
			<input class="inputReadOnly"  type='number' value='' readOnly="readOnly" />{{contract_price}} 元
          </div>
        </div>
        <div class="row" >
          <div class="left" >支付方式</div>
          <div class="right zhifufangshi">
            两次支付(定金, 尾款)
          </div>
        </div>
        <div class="row" >
          <div class="left" >定金</div>
          <div class="right" >
			<input class="inputReadOnly" type='number' value='' readOnly="readOnly"/>{{contract_deposit}} 元
          </div>
        </div>
      </div>

      <div class="other_info" >
        <div class="row">
          <a href="http://localhost:10066/edit_contract_skill_req">
            <div class="left" >服务项目</div>
            <div class="extra_text" >
              <p>已选
            <span class="extra_i" > 1
            </span>
            项</p>
            </div>
            <mip-img layout="responsive" width="16" height="16" class="jt" src='i/jt-right2.png' ></mip-img>
          </a>
        </div>
        <div class="row">
          <a href="http://localhost:10066/edit_contract_extra">
            <div class="left" >补充条款</div>
            <div class="extra_text" v-model="contract_extra" ></div>
            <mip-img layout="responsive" width="16" height="16" class="jt" src='i/jt-right2.png' ></mip-img>
          </a>
        </div>
        <div class="row" >
          <div class="left" >上户地点</div>
          <div class="right" >
            <textarea class="input_address" v-model="contract_location" type='text' value='' placeholder='请输入上户的详细地址' ></textarea>
          </div>
        </div>
      </div>

      <div class="contract_info">
        <div class="sub_head" >合同信息</div>
        <div class="contract_row">
          <span>《菩提果母婴护理服务合同》</span>
          <div class="extra_text_xx" >详细</div>
          <mip-img layout="responsive" width="16" height="16" class="jt_xx" src='i/jt-right2.png' ></mip-img>
        </div>
      </div>

      <div class="submit">
        <input class="btn" type="submit" value="我同意以上所有条款，提交">
      </div>

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
      body {

      }
      .root {
        background: #f2f2f2;
        padding-bottom: 30px;
      }
      .yifang {
        width: 100%;
        height: 90px;
        margin: 0 auto;
        position: relative;
        background-color: #fff;
        margin-bottom: 10px;
      }
      .bingfang {
        width: 100%;
        height: 90px;
        margin: 0 auto;
        position: relative;
        background-color: #fff;
      }
      .jiafang {
        width: 100%;
        margin: 0 auto;
        position: relative;
        background-color: #fff;
        height: 450px;
      }
      .mama_info {
        background: #fff;
        position: relative;
        height: 85px;
        color:#333333;
        margin-bottom: 10px;
        font-size: 15px;
      }
      .mama_info_span {
        position:  absolute;
        left: 52px;
        top: 1px;
        width: 170px;

      }
      .mama_header {
        height: 65px;
        width: 65px;
        position:  absolute;
        top: 10px;
        left: 12px;
        blrder-radius: 4px;
      }
      .mama_name {
        position: absolute;
        left: 90px;
        top: 10px;
      }
      .mama_phone {
        position: absolute;
        left: 90px;
        top: 35px;
      }
      .mama_phone_a {
        text-decoration: none;
        color:#333333;
      }
      .mama_id_card {
        position: absolute;
        left: 90px;
        top: 60px;
      }
      .mama_name_b {
        position: absolute;
        left: 90px;
        top: 20px;
      }
      .mama_phone_b {
        position: absolute;
        left: 90px;
        top: 45px;
      }
      .ptg_info {
        background: #fff;
        margin-bottom: 10px;
        line-height: ;
        padding: 10px 0 10px 10px;
      }

      .shanghu_info {
        margin-bottom: 10px;
        background:#fff;
        margin-top: -10px;
        /* position: relative; */
      }

      .other_info {
        background:#fff;
        position: relative;
        width: 100%;
        margin: 10px auto 0;
      }

      .row {
        overflow: hidden;
        cursor: pointer;
        background: #fff;
        position: relative;
        height: 44px;
        line-height: 44px;
        border-bottom: 1px solid #f2f2f2;
        overflow: hidden;
        padding-left: 10px;
        font-size: 15px;
      }

      .row_address {
        overflow: hidden;
        cursor: pointer;
        background: #fff;
        position: relative;
        padding-left: 10px;
        height: 70px;
        line-height: 40px;
        overflow: hidden;
        font-size: 15px;
      }

      .row .left {
        position: absolute;
        display:  inline-block;
        width: 105px;
        float: left;
        clear: left;
      }

      .left_address {
        width: 80px;
        float: left;
        clear: left;
        line-height: 0px;
      }

      .row .right {
        position: absolute;
        float: left;
        display: inline-block;
        left: 100px;
      }

      .contract_info {
        margin-bottom: 10px;
        position: relative;
        height: 100px;
      }

      .sub_head {
        line-height: 41px;
        padding-left: 10px;
        color:#888888;
        height:41px;
        background:#f2f2f2;
        position: relative;
        top: 0;
      }

      .contract_row {
        background: #fff;
        cursor: pointer;
        position: relative;
        padding-left: 5px;
        height: 44px;
        line-height: 44px;
        overflow: hidden;
        font-size: 15px;
      }

      .jt {
        width: 16px;
        height: 16px;
        position: absolute;
        right: 15px;
        top: 14px;
      }
      .jt_xx {
        width: 16px;
        height: 16px;
        position: absolute;
        right: 8px;
        top: 14px;
      }

      .btns {
        margin-top: 10px;
      }
      .submit {
        width: 80%;
        margin: 0 auto;
      }

      .btn {
        background: #09bb07;
        color: #fff;
        border-radius: 4px;
        cursor: pointer;
        text-align: center;
        font-size: 17px;
        width: 100%;
        height: 40px;
        position: relative;
        border-style: none;
        margin: 0 auto;
      }

      .btn2 {
        background: #fff;
        color: #333;
        width: 200px;
        line-height:;
        border-radius: 4px;
        cursor: pointer;
        margin: 10px auto 10px auto;
        text-align: center;
      }

      .clear {
        clear: both;
      }

      .input {
        border: none;
        width: 150px;
        font-size: 15px;
        height: 24px;
        display: inline-block;

      }
      .input_sc {
        border: none;
        line-height:;
        width: 70px;
        font-size: 15px;
      }
      .input_date {
        border: none;
        line-height: ;
        width: 170px;
        height:40px;
        font-size: 15px;
        /*background-image: url(assets/i/card_jf.png);*/
        background-size: 0;
      }

    .inputReadOnly {
        border: 0;
        line-height: .;
        width: 70px;
        color:#b2b2b2;

      }
    .input_address {
        margin-top: 7px;
        border: none;
        display: inline-block;
        width: 200px;
        height: 30px;
        resize:none;
      }
      .extra_text {
        float: right;
        right: 25px;
        color:#888888;
        font-size: 15px;
        position: absolute;
        width: 80px;
      }
      .extra_text_xx {
        float: right;
        color: #888888;
        font-size: 15px;
        position: absolute;
        right: 15px;
        top: 1px;
        width: 40px;
      }
      .extra_i {
        color: #09bb07;
        display: inline-block;
        margin: 0 3px;
        position: relative;
        width: 6px;
        text-align: center;
      }
    .radio {
        display: inline-block;
      }
    .radio_toggle_quantian {
        display: inline-block;
        opacity: 1;
        position:relative;
        width: 20px;
        z-index: 999;
      }
    .radio_toggle_baiban {
        display: inline-block;
        opacity: 1;
        position:relative;
        width: 20px;
        z-index: 999;
        left: 45px;
      }
    .radio_img_1 {
        position: absolute;
        left: 105px;
        width: 23px;
        top: 10px;
      }
    .radio_img_2 {
        position: absolute;
        left: 180px;
        width: 23px;
        top: 10px;
      }
    .radio_img_3 {
        position: absolute;
        left: 162px;
        width: 23px;
        top: 10px;
      }
    .id_photo {
        width: 90%;
        height: 110px;
        border-radius: 3px;
        margin-left: 5%;
        margin-right: 5%;
        margin-bottom: -4px;
      }

      .jiafang .row_photo {
        overflow: hidden;
        cursor: pointer;
        background: #fff;
        position: relative;
        padding-top: 10px;
        line-height: 25px;
        padding-bottom: 5px;
        overflow: hidden;
        width:50%;
        float:left;
        text-align: center;
        font-size: 15px;
      }

    .pho_back {
        position: absolute;
        top:10px;
        left:5%;
        height:110px;
        width:90%;
        background:black;
        opacity:0.2;
        border-radius: ;
      }
      .identity {
        width:30px;
        position:absolute;
        top:47px;
        left:40%;
      }
      .quantian {
        line-height: 40px;
        display: inline-block;
        margin-right: 24px;
        margin-left: 30px;
        position: absolute;
        top: 2px;
      }
      .baiban {
        line-height: 40px;
        display: inline-block;
        margin-right: 24px;
        margin-left: 5px;
        position: absolute;
        left: 90px;
        top: 2px;
      }
      .zhifufangshi {
        color: #b2b2b2;
      }
      .shanghu_info input[type='radio'] {
        display: inline;
        width: 40px;
        float: left;
        position: absolute;
        top: 15px;
        margin-left: -35px;
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


API.uploadFile = function(data, cb) {
  API.wrapRet_(
    '/api/upload_image', 
    {
      'data': data,
      'target': 'media/image-[md5].jpg'
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
	console.log('1111:',pdata);
	var data = pdata.order;
	var master_price = data.master.price_26day;//月嫂价格

	var master_price = !!data.contract_is_offer_allday_service ? 
	data.master.yuesao_allday_price : 
	data.master.yuesao_daytime_price;
	master_price = master_price / 100;

	var price = Math.round(master_price /26 * data.contract_shanghu_length);//通过月嫂价格和上户时长计算的总金额
	var deposit = Math.round(master_price /26 * data.contract_deposit_min * data.contract_shanghu_length);//通过月嫂价格和上户时长计算的订金
	if(data.contract_shanghu_length == 0){
	  	price = 0;
		deposit = 0;
		//master_price = 0;
	}else if(price != data.contract_price) {
		 price = data.contract_price;
		deposit = data.contract_deposit;
		master_price = Math.round(data.contract_price / data.contract_shanghu_length * 26 );
	}

    return {
		  master: pdata.order.master,
		  	contract_mama_name: data.contract_mama_name,
			contract_mama_phone_number: data.contract_mama_phone_number,
			contract_mama_id_card: data.contract_mama_id_card,
			contract_shanghu_at: data.contract_shanghu_at,
			contract_shanghu_length: data.contract_shanghu_length,
			contract_location: data.contract_location,
			contract_price: price,
			contract_master_price: master_price,
			contract_deposit: deposit,
			contract_is_pay_monthly: !!data.contract_is_pay_monthly,
			contract_is_offer_allday_service: data.contract_is_offer_allday_service,
			is_show_pay_monthly_btn: data.contract_shanghu_length >= 42 ? true : false,
			hardcode_deposit: data.hardcode_deposit,
			contract_mama_id_card_list: data.contract_mama_id_card_list,
			pics:[],
		 

    }
  },
  computed: {
	amount: function () {
																														
	},
    
  },
  methods: {
    init () {
      console.log('should loading');
      console.log(this.dataJson);
	  
    },

    load_data () {
      console.log('should set data');

    },
  change () {
    var pic = document.getElementById("preview"),
        file = document.getElementById("f");

    var ext=file.value.substring(file.value.lastIndexOf(".")+1).toLowerCase();

     // gif在IE浏览器暂时无法显示
     if(ext!='png'&&ext!='jpg'&&ext!='jpeg'){
         console.warn("图片的格式必须为png或者jpg或者jpeg格式！"); 
         return;
     }
       this.html5Reader(file);
     
},
uploadFile_(myBase64, fn){

  API.uploadFile(myBase64, function(isOk, res){
	console.log(res);
  });

},
html5Reader (file){

             var that = this;
     var file = file.files[0];
  //   var reader = new FileReader();
  //   reader.readAsDataURL(file);
   //  reader.onload = function(e){

  //       var pic = document.getElementById("preview").childNodes[1];
  //       pic.src=this.result;
  //   }

					function toDataUrl(url, callback) {
					    var xhr = new XMLHttpRequest();
					    xhr.onload = function() {
					        var reader = new FileReader();
					        reader.onloadend = function() {
					            callback(reader.result);
					        };
					        reader.readAsDataURL(xhr.response);
					    };
					    xhr.open('GET', url);
					    xhr.responseType = 'blob';
					    xhr.send();
					}
					function normalImageSize(w,h) {
						var nw = 800, nh = 1000;
						if (w <= nw && h <= nh) {
							return [w,h];
						}
						if (w >= h) {
							nh = h / (w/nw);
						} else {
							nw = w / (h/nh);
						}
						return [nw, nh];
					}
					function toDataUrl_v2(file, callback) {
						// ref https://sebastianblade.com/browser-side-image-compress-and-upload/
						// console.warn("2");

						var reader 	= new FileReader();
						var image 	= new Image();
						var canvas 	= document.createElement('canvas');
						var context = canvas.getContext('2d');

						image.addEventListener('load', function () {  
						  	// console.warn("5");
						  	// 规范图片尺寸
							var S = normalImageSize(image.naturalWidth,image.naturalHeight);
							canvas.width = S[0];
							canvas.height = S[1]; 							 
							// 将图片绘制到 canvas 画布上
							context.drawImage(image, 0, 0, S[0],S[1]);
							var quality = 30;
							var filetype = 'image/jpeg';
							compressedImageDataURL = canvas.toDataURL(filetype, quality/100);
							callback(compressedImageDataURL);
						});

						image.addEventListener('error', function () {  
						  	console.warn('Image load error');
						});
					    reader.onloadend = function(e) {
					    	// console.warn("4");
							var dataURL = e.target.result;
							// fileReader.result (data:image/png;base64,iVBORw0KG...)
							image.src = dataURL;

					    };

				//	    var xhr = new XMLHttpRequest();
				//	    xhr.onload = function() {
							// console.warn("3");
					        reader.readAsDataURL(file);
				//	    };
				//	    xhr.open('GET', url);
				//	    xhr.responseType = 'blob';
				//	    xhr.send();

					}


			    		console.log(file);
					toDataUrl_v2(file, function(myBase64) {
			    		// console.warn(6);
                         console.log(myBase64);
						 that.uploadFile_(myBase64, 'id_card_zheng');
		    
					});






 }
  }


}
</script>
