<template>
  <div>
    <router-view /><!--将下方的li标签设置好样式，将实现与android中fragment相同的功能-->
    <ul>
      <li><router-link :to="{name: 'list'}">新闻列表</router-link></li>
      <li><router-link :to="{name: 'user'}">个人中心</router-link></li>
    </ul>
  </div>



</template>
<script>

    export default {
        name:"Home"
    }
</script>
<style scoped>

</style>
