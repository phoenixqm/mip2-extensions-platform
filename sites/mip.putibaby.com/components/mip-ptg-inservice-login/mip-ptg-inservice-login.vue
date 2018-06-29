<template>
  <div class="wrapper">
    <Oauth :config="config" ref="oauth" @login="login" @logout="logout">
        <div slot="content" slot-scope="oauth">
            <div v-if="oauth.user">
                <p>hi，{{oauth.user.nickname}}，你上次登录时间为{{oauth.user.lasttime}}</p>
                <p><a href="/order/list.html" data-type="mip">订单中心</a></p>
                <p @click="toLogout">退出</p>
            </div>
            <div v-else>你还没有<span @click="toLogin" style="color: #f00">登录</span>哦</div>
        </div>
    </Oauth>
  </div>
</template>

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


API.hideFinishedOrder = function(orderId, cb) {
  API.wrapRet_(
    '/api/hide_finished_order', {
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

    // return {
    //     // mip-inservice-login组件的属性数据
    //     config: {
    //         appid: '熊掌号ID',
    //         clientId: '熊掌号开发者ID',
    //         endpoint: '后端endpoint'
    //         // 设置自动登录
    //         autologin: true
    //     }
    // }
    console.log(this);
    var pdata = JSON.parse(this.dataJsonstr);
    console.log(pdata.list);
    return {
      config:pdata
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
    toLogin() {
        console.log('去登录');
        // 调用 mip-inservice-login组件的登录方法
        this.$refs.oauth.login();
    },
    toLogout() {
        console.log('去登出');
        // 调用 mip-inservice-login组件的登录方法
        this.$refs.oauth.logout();
    },
    login(data) {
        // 收到mip-inservice-login组件的登录事件
        console.log('已登录');
    },
    logout() {
        // 收到mip-inservice-login组件的登出事件
        console.log('已登出')
    }
  }


}
</script>
