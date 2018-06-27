
<template>
<div class="root">
<div id='fullScreen'></div>

<div id='floatLayer'>
    <p>{{ msg }}</p>
    <p><button @click="cancelConfirm">取消</button></p>
    <p><button @click="okConfirm">确定</button></p>
</div>


</div>
    

</template>


<style scoped>
.wrapper {
  margin: 0 auto;
  text-align: center;
}
  /*人为制造一个占据整个屏幕的Div,其透明度为0.7且z-index为9999使之前的页面被压在底层无法点击*/
#fullScreen
{
    position: fixed;
    width: 100%;
    height: 100%;
    left: 0;
    top: 0;
    opacity: 0.7;
    background-color: black;
    z-index: 9999;
}
/*浮层,可随意设置大小宽高，但是z-index必须比上面fullScreen大才能显示出来*/
#floatLayer
{
    position: fixed;
    width: 500px;
    height: 500px;
    left: 34%;
    top: 15%;
    background-color: white;
    z-index: 10000;
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
  //console.log(ret);
    if(ret.success) cb(true, ret.data);
    else cb(false, ret.error);
  })  
  .catch(e => {
    console.error(e.message); 
    cb(false, e.message);
  });
}


export default {
  mounted () {
    console.log('This is master card component !')
  },
   firstInviewCallback () {
    this.init()
  },
  props: {
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
  data () {
    console.log(this);

  },
  computed: {
    
  },
  methods: {
    init () {
      console.log('should loading');
      this.reload_();
    },
    created() {

      this.reload_();
    },

    reload_() {

    }),
    cancelConfirm() {
      this.$emit(this.cancelevent);
    }),
    okConfirm() {
      this.$emit(this.okevent);
    }),
  }

}
</script>
