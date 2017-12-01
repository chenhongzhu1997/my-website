<template>
  <ul class="footer" :style="{'background-color':bg}">
      <li><router-link to="/movieList">电影</router-link>  </li>
      <li><router-link to="/music">音乐</router-link></li>
      <li><router-link to="/book">书籍</router-link></li>
      <li><router-link to="/photo">图片</router-link></li>
  </ul>
</template>
<script>
export default {
  props:['bg']
}
</script>
<style scoped>
.footer{
    display: flex;
    position:fixed;
    bottom:0;
    width:100%;
    height: 1rem;
    background: #0cf;
    line-height:1rem;
}
.footer li{
    color:#fff;
    text-align:center;
    flex-grow:1;
}
</style>


