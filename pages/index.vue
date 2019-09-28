<template>
<div class="page-index">
  <el-row>
    <el-col :span="5">
      <emenu/>
    </el-col>
    <el-col :span="19">
      <life/>
    </el-col>
  </el-row>
  <el-row>
    <el-col :span="24">
      <artistic/>
    </el-col>
  </el-row>
</div>
</template>

<script>
  import Emenu from '@/components/index/menu.vue'
  import Life from '@/components/index/life.vue'
  import Artistic from '@/components/index/artistic.vue'
  export default {
    components:{
      Emenu,
      Life,
      Artistic
    }
  }
</script>

<style lang="scss">
  @import "@/assets/css/index/index.scss";
</style>

<!--<template>-->
<!--  <div class="container">-->
<!--    <div>-->
<!--      <logo />-->
<!--      <h1 class="title">-->
<!--        tuangouapp-->
<!--      </h1>-->
<!--      <h2 class="subtitle">-->
<!--        My ultimate Nuxt.js project-->
<!--      </h2>-->
<!--      <div class="links">-->
<!--        <a-->
<!--          href="https://nuxtjs.org/"-->
<!--          target="_blank"-->
<!--          class="button&#45;&#45;green"-->
<!--        >-->
<!--          Documentation-->
<!--        </a>-->
<!--        <a-->
<!--          href="https://github.com/nuxt/nuxt.js"-->
<!--          target="_blank"-->
<!--          class="button&#45;&#45;grey"-->
<!--        >-->
<!--          GitHub-->
<!--        </a>-->
<!--      </div>-->
<!--    </div>-->
<!--  </div>-->
<!--</template>-->

<!--<script>-->
<!--import Logo from '~/components/Logo.vue'-->

<!--export default {-->
<!--  components: {-->
<!--    Logo-->
<!--  }-->
<!--}-->
<!--</script>-->

<!--<style>-->
<!--.container {-->
<!--  margin: 0 auto;-->
<!--  min-height: 100vh;-->
<!--  display: flex;-->
<!--  justify-content: center;-->
<!--  align-items: center;-->
<!--  text-align: center;-->
<!--}-->

<!--.title {-->
<!--  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,-->
<!--    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;-->
<!--  display: block;-->
<!--  font-weight: 300;-->
<!--  font-size: 100px;-->
<!--  color: #35495e;-->
<!--  letter-spacing: 1px;-->
<!--}-->

<!--.subtitle {-->
<!--  font-weight: 300;-->
<!--  font-size: 42px;-->
<!--  color: #526488;-->
<!--  word-spacing: 5px;-->
<!--  padding-bottom: 15px;-->
<!--}-->

<!--.links {-->
<!--  padding-top: 15px;-->
<!--}-->
<!--</style>-->
