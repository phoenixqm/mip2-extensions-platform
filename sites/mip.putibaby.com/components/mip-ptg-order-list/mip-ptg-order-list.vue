<template>
  <div class="root">
    <div class="row" v-for="order in list">
      <p class='row_p'>
        <span class="status">
                   {{ order.desc_str }}
            </span>
        <span class="row_header">
                   编号: {{ order.order_number }}
            </span>
      </p>
      <div class="info" @click="handleBtn(order)">
        <mip-img layout="responsive" width="85px" height="22px" class="header" v-bind:src="order.master.header.small"></mip-img>
        <!-- <mip-img layout="responsive" width="85px" height="22px"
                  class="header" src="i/age.png" ></mip-img> -->
        <span class="name">{{ order.master.name }}</span>
        <span class="price">￥{{ order.master.ptg_price }}</span>
        <div class="message">
          <mip-img layout="responsive" width="85px" height="22px" class="age_img" src="i/age.png"></mip-img>
          <span class="age">{{ order.master.age }}岁</span>
          <mip-img layout="responsive" width="85px" height="22px" class="work_year_img" src="i/work_year.png"></mip-img>
          <span class="work_year">{{ order.master.work_year }}年</span>
          <mip-img layout="responsive" width="85px" height="22px" class="jiguan_img" src="i/jiguan.png"></mip-img>
          <span class="jiguan">{{ order.master.jiguan }}</span>
        </div>
      </div>
      <div class="row_footer">
        <div class="btn_list">
          <div class="tuijianBtn" v-if="order.showBtn_tuijian" @click="handleBtn_tuijian(order)">推荐</div>
          <div class="tuijianBtn" v-if="order.showBtn_shipinyuyue" @click="handleBtn_shipinyuyue(order)">发起视频预约</div>
          <div class="tuijianBtn" v-if="order.showBtn_qianyue" @click="handleBtn_qianyue(order)">签约</div>
          <div class="" v-if="order.showBtn_chakanshipin" @click="handleBtn_chakanshipin(order)">查看视频</div>
          <div class="tuijianBtn" v-if="order.showBtn_wodeyuyue" @click="handleBtn_wodeyuyue(order)">我的预约</div>
          <div class="tuijianBtn" v-if="order.showBtn_buheshi" @click="handleBtn_buheshi(order)">不合适</div>
          <div class="tuijianBtn" v-if="order.showBtn_shanchu" @click="handleBtn_shanchu(order)">删除</div>
          <div class="tuijianBtn" v-if="order.showBtn_dianhualianxi" @click="handleBtn_dianhualianxi(order)">电话联系</div>
          <div class="tuijianBtn" v-if="order.showBtn_nidinghetong" @click="handleBtn_nidinghetong(order)">拟定合同</div>
          <div class="tuijianBtn" v-if="order.showBtn_chakanhetong" @click="handleBtn_chakanhetong(order)">查看合同</div>
          <div class="tuijianBtn" v-if="order.showBtn_jiaodingjin" @click="handleBtn_jiaodingjin(order)">交定金</div>
          <div class="tuijianBtn" v-if="order.showBtn_shanghu" @click="handleBtn_shanghu(order)">上户</div>
          <div class="tuijianBtn" v-if="order.showBtn_lianxikefu" @click="handleBtn_lianxikefu(order)">联系客服</div>
          <div class="tuijianBtn" v-if="order.showBtn_fukuan" @click="handleBtn_fukuan(order)">付款</div>
          <!-- <div class="btn tuijianBtn" v-if="order.showBtn_xuqian" @click="handleBtn_xuqian(order)">续签</div> -->
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

body {
  background-color: #F1F5E2 !important;
}

.root {
  background-color: #F1F5E2;
  padding-top: 1px;
}

.row {
  background: #fff;
  margin-top: 10px;
  position: relative;
  border: 1px solid #ddd;
  border-radius: 3px;
}

.row_p {
  margin: 0px;
  padding: 0px;
  line-height: 30px;
  border-bottom: 1px solid #eee;
}

.row_header {
  height: 30px;
  line-height: 30px;
  margin-right: 10px;
  color: #666;
  cursor: pointer;
  float: right;
  font-size: 13px;
}

.row_footer {
  border-top: 1px solid #eee;
  border-bottom: 1px solid #eee;
  background-color: #fff;
  height: 30px;
  padding-right: 10px;
}


.status {
  height: 30px;
  line-height: 30px;
  padding-left: 10px;
  color: #666;
  cursor: pointer;
  font-size: 13px;
}

.btn_list {
  float: right;
  text-align: right;
}

.tuijianBtn {
  border: 1px solid #afd03b;
  display: inline-block;
  border-radius: 3px;
  line-height: 1;
  font-size: 10px;
  padding: 3px 3px;
  margin: 5px 0px 8px 1px;
  color: #afd03b;
  cursor: pointer;
}

.info {
  background: #fff;
  position: relative;
  height: 68px;
  overflow: hidden;
  cursor: pointer;
}

.header {
  width: 68px;
  height: 68px;
  position: absolute;
  top: 0px;
  left: 0px;
}

.name {
  font-size: 15px;
  color: #666;
  position: absolute;
  top: 15px;
  left: 78px;
}

.price {
  font-size: 16px;
  font-weight: bold;
  color: red;
  position: absolute;
  top: 15px;
  right: 10px
}

.message {
  font-size: 13px;
  color: #999;
  position: absolute;
  top: 40px;
  left: 78px;
}

.age_img {
  width: 13px;
  height: 10px;
  position: relative;
  top: 0;
  display: inline-block;
}

.age {
  display: inline-block;
  margin-right: 5px;
}

.work_year_img {
  width: 13px;
  height: 10px;
  position: relative;
  top: 0;
  display: inline-block;
}

.work_year {
  display: inline-block;
  margin-right: 5px;
}

.jiguan_img {
  width: 13px;
  height: 10px;
  position: relative;
  top: 0;
  display: inline-block;
}

.btn {
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

API.rejectInterview = function(orderId, cb) {
  API.wrapRet_(
    '/api/reject_interview', {
      'id': orderId
    },
    cb);
};

API.hideFinishedOrder = function(orderId, cb) {
  API.wrapRet_(
    '/api/hide_finished_order', {
      'id': orderId
    },
    cb);
};

API.doShanghu = function(orderId, cb) {
  API.wrapRet_(
    '/api/do_shanghu', {
      'id': orderId
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
      list: pdata.list,
      state: {
        showTuijianBtn: true,
        show_confirm: false

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
      location.reload();
      var href = self.location.href;
      if (href.indexOf('?') >= 0) {
        self.location.href = href + '&_=' + Math.random();
      } else {
        self.location.href = href + '?_=' + Math.random();
      }
    },
    handleBtn(order){
      window.location.href = '/master_card?mcode=' + order.master.mcode;
    },
    handleBtn_tuijian(order) {
      window.location.href = '/master_card?mcode=' + order.master.mcode;
    },

    handleBtn_shipinyuyue(order) {
      window.location.href = '/video_interview_master?master_id=' + order.master.id;
    },
    handleBtn_qianyue(order) {
      window.location.href = '/show_master?u=' + order.master.username;
    },
    handleBtn_chakanshipin(order) {
      window.location.href = '/show_my_qs_list?id=' + order.id;
    },
    handleBtn_wodeyuyue(order) {
      window.location.href = '/show_my_realtime_video_interview?id=' + order.id;
    },
    handleBtn_buheshi(order, skip) {

      var self = this;
      if (skip) {
        API.rejectInterview(order.id, function(isOk, data) {
          if (isOk) {
            self.reload_();
          } else {
            console.warn(data);
          }
        });

      } else {

        var ele = document.getElementById('ptgconfirm');
        // console.log(ele);
        MIP.viewer.eventAction.execute('doshow', ele, { 
          el_id: 'orderlist', 
          title:'提示消息',
          msg: '确定不合适?',
          from: this.handleBtn_buheshi, 
          data: order });

      }

    },
    handleBtn_shanchu(order, skip) {
      var self = this;
      // if(!confirm('确定要删除?')) return;
      if (skip) {
        API.hideFinishedOrder(order.id, function(isOk, data) {
          if (isOk) {
            self.reload_();
          } else {
            console.warn(data);
          }
        });

      } else {

        var ele = document.getElementById('ptgconfirm');
        // console.log(ele);
        MIP.viewer.eventAction.execute('doshow', ele, { 
          el_id: 'orderlist', 
          title:'提示消息',
          msg: '确定要删除?',
          from: this.handleBtn_shanchu, 
          data: order });

      }

    },
    handleBtn_dianhualianxi(order) {
      window.location.href = 'tel:' + order.master.phone_number;
    },
    handleBtn_nidinghetong(order) {
      window.location.href = '/edit_contract?id=' + order.id;
    },
    handleBtn_chakanhetong(order) {
      window.location.href = '/edit_contract?id=' + order.id + '&readonly=1';
    },
    handleBtn_jiaodingjin(order) {
      window.location.href = '/pay/v2_do_pay?order_id=' + order.id;
    },
    handleBtn_shanghu(order) {
      // var self = this;
      // API.doShanghu(order.id, function(isOk, data) {
      //   if (isOk) {
      //     self.reload_();
      //   } else {
      //     console.warn(data);
      //   }
      // });
      var self = this;
      if (skip) {
        API.doShanghu(order.id, function(isOk, data) {
          if (isOk) {
            self.reload_();
          } else {
            console.warn(data);
          }
        });

      } else {

        var ele = document.getElementById('ptgconfirm');
        // console.log(ele);
        MIP.viewer.eventAction.execute('doshow', ele, { 
          el_id: 'orderlist', 
          title:'提示消息',
          msg: '确定要现在执行上户?',
          from: this.handleBtn_shanghu, 
          data: order });

      }
    },

    handleBtn_lianxikefu(order) {
      window.location.href = 'tel:400-618-8835';
    },
    handleBtn_fukuan(order) {
      window.location.href = '/pay/v2_do_pay?order_id=' + order.id;
    },
    handleBtn_xuqian(order) {
      window.location.href = '/v2_edit_xudan_yuesao_contract?order_id=' + order.id;
    },
  }


}
</script>
