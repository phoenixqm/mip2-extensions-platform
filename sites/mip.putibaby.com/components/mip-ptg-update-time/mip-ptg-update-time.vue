
<template>
<div class="root">
  <div class="text">
    <p class="title">实时视频面试，可直接与护理师视频交流，与现场面试效果相似，但不受时间空间限制，免去车马劳顿，更加方便。</p>
    <p class="title">需要先提交预约，由菩提果帮您协调视频时间。</p>
    <mip-img layout="responsive" width="85px" height="22px" class="video_interview" src="i/v2/video_interview.png"></mip-img>
  </div>
  <textarea class="textarea hide" name="mcode" placeholder=""><%= data.mcode %></textarea>
  <textarea class="textarea" name="info" placeholder="您方便的时间段，可不填"></textarea>
  <input type="submit" name="提交" class="submit" @click="handleSubmit_">

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
}
body {
  background-color: #F1F5E2;
}


p {
  margin: 0px;
  padding: 0px;
  font-family: '黑体';
}

.root {
  padding: 15px;
}

.title {
  margin-top: 15px;
  color: #666;
}

.gray {
  color: #666;
}

.name {
  /*width: 100px;*/
  border-radius: 5px;
  border: solid 1px #ddd !important;
}

table tr td {
  height: 30px;
}

.video_interview {
  display: block;
  position:relative;
  width: 100%;
  height: 152px;
  margin-top: 15px;
}

textarea {
  -webkit-appearance:none;
  width: 92%;
  height: 94px;
  border-radius: 5px;
  color: #666;
  /*border: solid 1px #ddd !important;*/
  margin-top: 15px;
  font-size: 14px !important;
  padding: 10px;
  position:relative;
  display:inline-block;
  border-color:#fff;
}

textarea.hide {
  display: none;
  -webkit-appearance:none;
}

.submit {
  outline: none;
  -webkit-appearance: none;
  position:relative;
  border-radius: 0;
  width: 89.2%;
  height: 47px !important;
  line-height: 20px;
  text-align: center;
  background-color: #afd03b !important;
  color: #fff !important;
  margin: 0 auto;
  font-size: 18px;
  border-style:none;
  top:30px;
  left:50%;
  margin-left:-44.6%;
  border-radius:5px;
  margin-bottom:50px;
}

.text {
  background-color: #fff;
  padding: 15px;
  padding-top: 1px;
  font-family:'黑体';
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
      if (ret.success) cb(true, ret.data);
      else cb(false, ret.error);
    })
    .catch(e => {
      console.error(e.message);
      cb(false, e.message);
    });
}

API.uploadFile = function(data, cb) {
  API.wrapRet_(
    '/api/upload_image', {
      'data': data,
      'target': 'media/image-[md5].jpg'
    },
    cb);
};

export default {
  mounted() {

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

    var data = pdata.order;

    return {
      content: '',
    
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

    handleSubmit_() {
     
	  var mcode = JSON.parse(this.dataJsonstr).mcode;
      var url = '/update_time_ok?cmode=' + mcode + '&intro=';

      window.location.replace(url);

    },
  }
}
</script>
