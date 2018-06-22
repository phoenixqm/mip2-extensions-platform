
<template>
<div>
    <div  v-for="order in list">
        <p class='row_p'>
            <span class="status">
                   {{ order.desc_str }}
            </span>
              <span class="row_header">
                   编号: {{ order.order_number }}
            </span>
        </p>  

         <div class="info">
		 <mip-img layout="responsive" width="85px" height="22px"
                  class="header" v-bind:src="order.master.header.small" ></mip-img>  
               <!-- <mip-img layout="responsive" width="85px" height="22px"
                  class="header" src="i/age.png" ></mip-img> --> 
                  <span class="name">{{ order.master.name }}</span>
            <span class="price">￥{{ order.master.ptg_price }}</span>
            <div class="message">
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

        </div> 
        <div class="row_footer">
               <div class="btn_list">
                  <div class="btn tjBtn">推荐</div>
                  <div class="btn showBtn">查看合同</div>
                  <div class="btn depositBtn">交定金</div>
                  <div class="btn payBtn">付款</div>
                  <div class="btn shanghuBtn">续签</div>
                  <div class="btn xudanBtn">续签</div>
                  <div class="btn delBtn">删除</div>
                  <div class="btn callBtn">联系客服</div>
               </div>
              <div class="clear"></div>
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
   background-color: #f3f3f3;
}
.row{
   background: #fff;
   margin-top: 10px;
   position: relative;
}

.row_p{
   margin: 0px;
   padding: 0px;
   line-height: 30px;
   border: 1px solid #eee;
}

.row_header{
   height: 30px;
   line-height: 30px;
   margin-right: 10px;
   color: #999;
   cursor: pointer;
   float: right;
}
.row_footer {
   border-top: 1px solid #eee;
   border-bottom: 1px solid #eee;
   background-color: #fff;
   width: 100%;
   height: 40px;
}


.status{
   height: 30px;
   line-height: 30px;
   padding-left: 10px;
   color: #999;
   cursor: pointer;
}

.btn_list{
   float: right;
   text-align: right;
}

.info{
   background: #fff;
   position: relative;
   height: 72px;
   overflow: hidden;
   cursor: pointer;
}

.header{
   width: 50px;
   height: 50px;
   position: absolute;
   top: 10px;
   left: 10px;
   border-radius: 5px;
}

.name{
   font-size: 16px;
   font-weight: bold;
   color: #333;
   position: absolute;
   top: 15px;
   left: 70px;
}

.price{
   font-size: 16px;
   font-weight: bold;
   color: red;
   position: absolute;
   top: 15px;
   left: 130px
}

.message{
   font-size: 14px;
   color: #666;
   position: absolute;
   top: 40px;
   left: 70px;
}

.age_img{
   width: 14px;
   height: 14px;
   position: relative;
   top: 0;
   display: inline-block;
   margin-right: 2px;
}

.age{
   display: inline-block;
   margin-right: 10px;
}

.work_year_img{
   width: 14px;
   height: 14px;
   position: relative;
   top: 0;
   display: inline-block;
   margin-right: 2px;
}
.work_year{
   display: inline-block;
   margin-right: 10px;
}

.jiguan_img{
   width: 14px;
   height: 14px;
   position: relative;
   top: 0;
   display: inline-block;
   margin-right: 2px;
}

.btn{
   border: 1px solid #ccc;
   display: inline-block;
   border-radius: 5px;
   line-height: 1;
   font-size: 14px;
   padding: 3px 5px;
   margin: 8px 5px 8px 5px;
   color: #666;
   background: #eee;
   cursor: pointer;
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
