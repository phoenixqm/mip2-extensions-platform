<template>
  <div class="root">
    <div class='header'>
      支付订单{{ data.order_number }}，{{ data.text }}
    </div>
    <div class='row'>
      <div class="left">支付金额</div>
      <div class="right">{{ (data.amount/100).toFixed(2) }} 元</div>
    </div>
    <div class="header">
      支付方式
    </div>
    <div class="row" @click="useBalancePay">
      <div class="left">&nbsp;&nbsp;&nbsp;&nbsp;- 余额支付</div>
      <div class="right">{{ (data.reward_balance/100).toFixed(2) }} 元</div>
      <div :calss="{'checked' : balanceChecked , 'unchecked' : !balanceChecked}" />
    </div>

    <div class="row" @click="useBankPay">
      <div class="left">&nbsp;&nbsp;&nbsp;&nbsp;- 银行汇款</div>
      <div class="right">查看说明</div>
      <div class="icon go" />
    </div>
    <!-- <div class="btn" @click="doPay">确定支付</div> -->
<mip-data>
    <script type="application/json">
        {
            "payConfig":{
                "subject":"支付商品",
                "fee": {{ (data.amount/100).toFixed(2) }},
                "sessionId":"c8fbd3e0-a617-4eac-84b3-1f289c5ce857",
                "redirectUrl":"https://api.example.com/pay/verifypay",
                "endpoint":{
                    "baifubao":  "https://api.example.com/pay/baifubao",
                    "alipay":  "https://api.example.com/pay/alipay",
                    "weixin":  "https://api.example.com/pay/weixin"
                },
                "postData":{
				  "orderId": {{ data.order_number }},
                    "token": "xxxx",
                    "anydata":"anydata"
                }
            }
        }
    </script>
</mip-data>
<mip-inservice-pay m-bind:pay-config="payConfig" id="payDialog"></mip-inservice-pay>
<button on="tap:payDialog.toggle">确定支付</button>
    <p class="tip">温馨提示：如果您使用微信支付过程中遇到支付限额问题，建议您使用支付宝进行支付。如有疑问，请拨打菩提果客户服务电话： 400-618-8835。</p>

    
  </div>
</template>
<style scoped>
.wrapper {
  margin: 0 auto;
  text-align: center;
}

.root {
  background: '#f2f2f2';
}

.btn {
  background: '#FF6867';
  color: '#fff';
  cursor: 'pointer';
  lineHeight: 36px;
  textAlign: 'center';
  borderRadius: 4;
  margin: 30px 20px;
}

.row {
  height: 40px;
  lineHeight: 40px;
  position: 'relative';
  background: '#fff';
  borderBottom: '1px solid #ccc';
}

.header {
  lineHeight: 3px;
  paddingLeft: 10px;
  borderBottom: '1px solid #ccc';
}

.left {
  position: 'absolute';
  left: 10px;
}

.right {
  color: 'rgb(255, 51, 0)';
  position: 'absolute';
  right: 40px;
}

.icon {
  position: 'absolute';
  right: 10px;
  top: 5px;
  width: 30px;
  height: 30px;
  backgroundSize: 'contain';
}

.checked {
  /*backgroundImage: 'url(' + util.i('checked.png') + ')';*/
}

.unchecked {
  /*backgroundImage: 'url(' + util.i('unchecked.png') + ')';*/
}

.go {
  /*backgroundImage: 'url(' + util.i('jt-right.png') + ')';*/
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
