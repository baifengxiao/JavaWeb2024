<script setup type="module">

import {useRouter} from 'vue-router'

//创建动态路由对象
let router = useRouter()

//方法2,第二步，通过绑定的路径传参方法，确定路由和参数
let showDetail= (id,language)=>{

  //动态路由路径传参有下面2种方式
  // 1  使用拼接字符串方式传递路径参数，
  router.push(`showDetail/${id}/${language}`)
  // 2  或者  使用params，进行动态路由路径传参显示
  //   router.push({name:"showDetail",params:{id:id,language:language}})
}

//方法4
let showDetail2= (id,language)=>{
  /*uri键值对参数,需要使用query */
  router.push({path:"/showDetail2",query:{id:id,language:language}})
}
</script>

<template>
  <div>
    <h1>App页面</h1>
    <hr/>
<!--    路径拼接2个方法-->
    <!-- 方法1：路径传参 ，第一步，点击后根据router.js进行路由跳转  -->
    <router-link to="/showDetail/1/JAVA">showDetail路径传参显示JAVA</router-link>
<!--    方法2： 动态路由路径传参 ,第一步，绑定传参方法-->
    <button @click="showDetail(1,'JAVA')">showDetail动态路由路径传参显示JAVA</button>
    <hr/>

    <!-- 键值对参数2个方法 -->
<!--    方法3-->
    <router-link v-bind:to="{path:'/showDetail2',query:{id:1,language:'Java'}}">showDetail2键值对传参显示JAVA</router-link>

<!--    方法4-->
    <button @click="showDetail2(1,'JAVA')">showDetail2动态路由键值对传参显示JAVA</button>
    <hr>
    showDetail视图展示:<router-view name="showDetailView"></router-view>
    <hr>
    showDetail2视图展示:<router-view name="showDetailView2"></router-view>
  </div>
</template>

<style scoped>
</style>
