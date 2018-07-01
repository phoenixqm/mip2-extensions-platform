<template>
  <div class="root">
    <div class='header'>
      支付订单{{ data.order_number }}，{{ data.text }}
    </div>
    <div class='row'>
      <div class="left">应付金额</div>
      <div class="right">{{ (data.amount/100).toFixed(2) }} 元</div>
    </div>
    <div class='row'>
      <div class="left">优惠金额</div>
      <div class="right">{{ (data.coupon/100).toFixed(2) }} 元</div>
    </div>
    <div class='row'>
      <div class="left">实付金额</div>
      <div class="right">{{ (data.payamount/100).toFixed(2) }} 元</div>
    </div>    
    <div class="header">
      支付方式
    </div>
    <div class="row" @click="useBalancePay">
      <div class="left">余额支付</div>
      <div class="right">{{ (data.reward_balance/100).toFixed(2) }} 元</div>
      <div :calss="{'checked' : balanceChecked , 'unchecked' : !balanceChecked}" />
    </div>

    <div class="row" @click="useInservicePay">
      <div class="left">还需支付</div>
      <div class="right">{{ (data.payabal/100).toFixed(2) }} 元</div>
      <div :calss="{'checked' : balanceChecked , 'unchecked' : !balanceChecked}" />
    </div>
    <!-- <div class="btn" @click="doPay">确定支付</div> -->

    <mip-data>
        <script type="application/json">
            {
                "payConfig":{
                    "subject":"支付商品",
                    "fee": {{ (data.amount/100).toFixed(2) }},
                    "sessionId": "{{ data.sessionId }}",
                    "redirectUrl": "https://mip.putibaby.com/api/pay/verifypay",
                    "endpoint":{
                        "baifubao":  "https://mip.putibaby.com/api/pay/baifubao",
                        "alipay":  "https://mip.putibaby.com/api/pay/alipay",
                        "weixin":  "https://mip.putibaby.com/api/pay/weixin"
                    },
                    "postData":{
                        "orderId": {{ data.order_number }},
                        "token": "{{ data.token }}",
                        "anydata":{{ data.order_data }}
                    }
                }
            }
        </script>
    </mip-data>
    <mip-inservice-pay m-bind:pay-config="payConfig" id="payDialog"></mip-inservice-pay>
    <button on="tap:payDialog.toggle">确定支付</button>

    <p class="tip">温馨提示：如果您使用百度极速支付过程中遇到问题。请拨打菩提果客户服务电话： 400-618-8835。</p>

    
  </div>
</template>
<style scoped>
.wrapper {
  margin: 0 auto;
  text-align: center;
}

.root {
  background: #f2f2f2;
}

.btn {
  background: #FF6867;
  color: #fff;
  cursor: pointer;
  line-height: 36px;
  text-align: center;
  borderRadius: 4;
  margin: 30px 20px;
}

.row {
  height: 40px;
  line-height: 40px;
  position: relative;
  background: #fff;
  border-bottom: 1px solid #ccc;
}

.header {
  line-height: 3px;
  paddingLeft: 10px;
  border-bottom: 1px solid #ccc;
}

.left {
  position: absolute;
  left: 10px;
}

.right {
  color: rgb(255, 51, 0);
  position: absolute;
  right: 40px;
}

.icon {
  position: absolute;
  right: 10px;
  top: 5px;
  width: 30px;
  height: 30px;
  background-size: contain;
}

.checked {
  background-image: url('/i/checked.png');
}

.unchecked {
  background-image: url('/i/unchecked.png');
}

.go {
  background-image: url('/i/jt-right.png');
}

.tip {
  margin: 30px 20px;
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
    console.log('This is pty order pay component !');



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
      data:pdata
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

    },
    useBalancePay() {
      console.log('using balance');
    },
    useWxPay() {
      console.log('using wx');
    },
    useZfbPay() {
      console.log('using zfb');
    },
    useBankPay() {
      console.log('using bank');
    },
  }


}
</script>
