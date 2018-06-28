<template>
  <div v-if="show" class="root">
    <div id='fullScreen'></div>
    <div id='floatLayer'>
      <p class="msg">{{ msg }}</p>
      <span>
        <button class="btn_cal" @click="cancelConfirm">取消</button>
      </span>
      <span>
        <button class="btn_ok" @click="okConfirm">确定</button>
      </span>
    </div>
  </div>
</template>
<style scoped>
.wrapper {
  margin: 0 auto;
  text-align: center;
}



/* https://www.cnblogs.com/martianShu/p/5893355.html */

#fullScreen {
  position: fixed;
  width: 100%;
  height: 100%;
  left: 0;
  top: 0;
  opacity: 0.7;
  background-color: black;
  z-index: 9999;
}

#floatLayer {
  position: fixed;
  width: 80%;
  height: 150px;
  left: 10%;
  top: 25%;
  background-color: white;
  z-index: 10000;
  border-radius: 5px;
  padding-top: 50px;
  text-align: center;
}
.msg{
  margin-bottom: 20px;
}

.btn_cal{
  display:inline-block;
  width:50px;
  height:30px;
}
.btn_ok{
  display:inline-block;
  width:50px;
  height:30px;
  margin-left: 30px;
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
      //console.log(ret);
      if (ret.success) cb(true, ret.data);
      else cb(false, ret.error);
    })
    .catch(e => {
      console.error(e.message);
      cb(false, e.message);
    });
}


export default {
  mounted() {
    console.log('This is comfirm component !');
    var self = this;
    this.$element.customElement.addEventAction('doshow', function(event, str) {
      // console.log(event);
      // console.log(str);
      self.show = true;
      self.msg = event.msg;
      self.current_el_event = event;
      self.current_el_id = event.el_id;
      self.current_el_data = event.data;
    });
  },
  firstInviewCallback() {
    this.init()
  },
  props: {
    show: {
      type: Boolean,
      default: false
    },
    msg: {
      type: String,
      default: null
    },
    title: {
      type: String,
      default: null
    },
    okevent: {
      type: String,
      default: null
    },
    cancelevent: {
      type: String,
      default: null
    }
  },
  data() {
    console.log(this);
    return {
      show: false
    };

  },
  computed: {

  },
  watch: {
    show: function(val, oldVal) {
      console.log('new: %s, old: %s', val, oldVal);
    }
  },
  methods: {
    init() {
      console.log('should loading');
      this.reload_();
    },
    created() {

      this.reload_();
    },

    reload_() {

    },
    cancelConfirm() {

      var ele = document.getElementById(this.current_el_id);
      // console.log(ele);
      this.current_el_event.el_id = 'ptgconfirm';
      MIP.viewer.eventAction.execute('docancel', ele, this.current_el_event);
      this.current_el_event = {};
      this.current_el_id = '';
      this.current_el_data = {};
      this.show = false;
    },
    okConfirm() {
      var ele = document.getElementById(this.current_el_id);
      // console.log(ele);
      this.current_el_event.el_id = 'ptgconfirm';
      MIP.viewer.eventAction.execute('dook', ele, this.current_el_event);
      this.current_el_event = {};
      this.current_el_id = '';
      this.current_el_data = {};
      this.show = false;

    }
  }

}
</script>