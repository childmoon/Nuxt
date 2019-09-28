<template>
  <div class="search-panel">
    <el-row class="m-header-searchbar">
      <el-col
        :span="3"
        class="left">
<!--        src="//s0.meituan.net/bs/fe-web-meituan/e5eeaef/img/logo.png"-->
        <img
          src="@/static/startlogo.png"
          alt="美团">
      </el-col>
      <el-col
        :span="15"
        class="center">
        <div class="wrapper">
          <el-input
            v-model="search"
            @focus="focus"
            @blur="blur"
            @input="input"
            placeholder="搜索商家或地点"/>
          <button class="el-button el-button--primary"><i class="el-icon-search"/></button>
          <dl
            class="hotPlace"
            v-if="isHotPlace">
            <dt>热门搜索</dt>
            <!--v-for="(item,index) in searchList"-->
            <dd
              v-for="(item,index) in $store.state.home.hotPlace.slice(0,5)"
              :key="index">
              <a :href="'/products?keyword='+encodeURIComponent(item.name)">{{ item.name }}</a></dd>
<!--            :key="index">{{item}}</dd>-->
          </dl>
          <dl
            class="searchList"
            v-if="isSearchList">
            <dd
              v-for="(item,index) in searchList"
              :key="index">
              <a :href="'/products?keyword='+encodeURIComponent(item.name)">{{ item.name }}</a>
            </dd>
          </dl>
        </div>
        <p class="suggest">
          <a
            v-for="(item,idx) in $store.state.home.hotPlace.slice(0,5)"
            :key="idx"
            :href="'/products?keyword='+encodeURIComponent(item.name)">{{ item.name }}</a>
<!--          <a href="#">故宫博物院</a>-->
<!--          <a href="#">故宫博物院</a>-->
<!--          <a href="#">故宫博物院</a>-->
<!--          <a href="#">故宫博物院</a>-->
        </p>
        <ul class="nav">
          <li>
            <nuxt-link
              to="/"
              class="takeout">美团外卖</nuxt-link>
          </li>
          <li>
            <nuxt-link
              to="/"
              class="movie">猫眼电影</nuxt-link>
          </li>
          <li>
            <nuxt-link
              to="/"
              class="apartment">美团酒店</nuxt-link>
          </li>
          <li>
            <nuxt-link
              to="/"
              class="business">商家入驻</nuxt-link>
          </li>
        </ul>
      </el-col>
      <el-col
        :span="6"
        class="right">
        <ul class="security">
          <li><i class="refund"><p class="txt">随时退</p></i></li>
          <li><i class="single"><p class="txt">不满意免单</p></i></li>
          <li><i class="overdue"><p class="txt">过期退</p></i></li>
        </ul>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import _ from 'lodash'
export default {
data(){
  return{
    search:'',
    isFocus:false,
    // hotPlace:['杭州','杭州','杭州','杭州'],
    // searchList:['火锅','火锅','火锅','火锅']
    hotPlace:[],
    searchList:[]
  }
},
  computed:{
    isHotPlace(){
      return this.isFocus&&!this.search
    },
    isSearchList(){
      return this.isFocus&&this.search
    }
  },
  methods:{
    focus(){
      this.isFocus=true
    },
    blur(){
      // this.isFocus=false
      let self=this;
      setTimeout(function(){
        self.isFocus=false
      },200)
    },
    input:_.debounce(async function(){
      let self=this;
      let city=self.$store.state.geo.position.city.replace('市','')
      self.searchList=[]
      let {status,data:{top}}=await self.$axios.get('/search/top',{
        params:{
          input:self.search,
          city
        }
      })
      self.searchList=top.slice(0,10)
    },300)
  }
}
</script>

<style lang="css">

</style>
