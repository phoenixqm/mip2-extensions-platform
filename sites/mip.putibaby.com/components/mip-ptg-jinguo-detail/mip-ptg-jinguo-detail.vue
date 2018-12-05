
<template>
  <div class="root">

    <mip-img
      layout="responsive"
      width="16"
      height="16"
      class="jt"
      src="i/contract_jt.png"/>
    <mip-img
      layout="responsive"
      width="16"
      height="16"
      class="jt"
      src="i/contract_jt.png"/>
    <mip-img
      layout="responsive"
      width="16"
      height="16"
      class="jt"
      src="i/contract_jt.png"/>
    <mip-img
      layout="responsive"
      width="16"
      height="16"
      class="jt"
      src="i/contract_jt.png"/>
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

.root {
  background: #f4f4f4;
  padding-bottom: 30px;
  color: #666;
  font-size: 14px;
}
.jt_xx {
  width: 8px;
  height: 13px;
  position: absolute;
  right: 14px;
  top: 16px;
}

</style>

<script>


export default {
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
  data () {
  },
  computed: {

  },
  prerenderAllowed () {
    return true
  },
  mounted () {
  },
  methods: {
    init () {
    },
    load_data () {
    }
  }
}
</script>
