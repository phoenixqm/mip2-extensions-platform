<template>
    <div class="wrap">
        <h3>这是一个渲染片段示例</h3>
        <p>默认未登录，由用户交互（如点击按钮）触发登录/登出</p>
        <hr />
        <div v-if="info.isLogin">hi，{{info.userInfo.nickname}}，欢迎回来！<span  style="color:#f00;" on="tap:log.logout">退出</span></div>
        <div v-else>你没有<span  style="color:#f00;" on="tap:log.login">登录</span>哦。</div>
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
  props: {
    info: {
        type: Object,
        required: true
    }
  },
  mounted() {
    console.log('This is pty order pay component !');

    // 自定义login事件
    this.$element.customElement.addEventAction('login', event => {
        // 这里可以输出登录之后的数据

        // 获取用户信息
        event.userInfo;
        // 后端交互会话标识
        event.sessionId;
    });
    // 自定义exit事件
    this.$element.customElement.addEventAction('exit', event => {
        console.log('登出了');
    });

  },

  data() {

    // var pdata = JSON.parse(this.dataJsonstr);

    return {
      
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

  }


}
</script>
