
<template>
  <div class="root">
    <div class="yifang">

      <div class="">
        <div class="mama_name">乙方
          <span class="mama_info_span"> master.name </span>
        </div>
        <div class="mama_phone">电话
          <span class="mama_info_span">
            <a href="tel:400-618-8835"> master.phone_number </a>
          </span>
        </div>
        <div class="mama_id_card">身份证
          <span class="mama_info_span"> master.id_card 
          </span>
        </div>
      </div>
    </div>
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
