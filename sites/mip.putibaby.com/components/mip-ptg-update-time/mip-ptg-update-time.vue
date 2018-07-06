
<template>
<div class="root">
  <div class="text">
    <p class="title">实时视频面试，可直接与护理师视频交流，与现场面试效果相似，但不受时间空间限制，免去车马劳顿，更加方便。</p>
    <p class="title">需要先提交预约，由菩提果帮您协调视频时间。</p>
    <mip-img layout="responsive" width="85px" height="22px" class="video_interview" src="i/v2/video_interview.png"></mip-img>
  </div>
  <textarea class="textarea hide" name="mcode" placeholder=""><%= data.mcode %></textarea>
  <textarea class="textarea" name="info" placeholder="您方便的时间段，可不填"></textarea>
  <input type="submit" name="提交" class="submit">

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

p {
  margin: 0px;
  padding: 0px;
  font-family: '黑体';
}

body {
  background-color: #fff;
  font-family: Arial, 'Hiragino Sans GB', 'Microsoft Yahei', '微软雅黑', '宋体', 宋体, Tahoma, Arial, Helvetica, STHeiti;
}

* {
  margin: 0px;
  padding: 0px;
}

p {
  margin: 0px;
  padding: 0px;
  font-family: '黑体';
}

body {
  background-color: #F1F5E2;
}

.root {
  padding: 10px;
}

.title {
  margin: 10px 10px 10px 0px;
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
  width: 97%;
  height: 140px;
  margin-top: 20px;
  margin-bottom: 20px;
}

textarea {
  width: 100%;
  height: 100px;
  border-radius: 5px;
  color: #666;
  /*border: solid 1px #ddd !important;*/
  margin-top: 20px;
  font-size: 14px !important;
  padding: 10px;
}

textarea.hide {
  display: none;
}

.submit {
  outline: none;
  -webkit-appearance: none;
  border-radius: 0;
  width: 94.36%;
  height: 47px !important;
  line-height: 20px;
  text-align: center;
  background-color: #afd03b !important;
  color: #fff !important;
  margin: 0 auto;
  margin-top: 30px;
  font-size: 18px;
}

.text {
  background-color: #fff;
  padding: 10px;
  padding-top: 1px;
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
      rea: false,
      dateChecked: true,
      name: '',
      date: '',
      tuijian: true,
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

    Checked() {
      this.tuijian = !this.tuijian;

    },
    handleSubmit_() {
      if (this.name == '' || this.date == '') {
        this.rea = true;
        return;
      }
      if (this.tuijian == true) {
        var masterType = 'yuesao';
      } else {
        var masterType = 'yuersao';
      }
      var url = '/update_ycq_ok?name=' + this.name + '&ycq=' + this.date + '&masterType=' + masterType;

      window.location.href = url;

    },
  }
}
</script>
