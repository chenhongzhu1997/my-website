<template>
  <div class="header" :style="{backgroundColor:bg}">
      <button class="home" @click="goHome">首页</button>
      <slot name='title'>默认值</slot>
  </div>
</template>
<script>
export default {
  methods:{
      goHome(){
          this.$router.push('/');
      }
  },
  props:['bg']
}
</script>
<style scoped>
.header{
    height: 1rem;
    background:#0cf;
    position: fixed;
    top:0;
    width:100%;
    line-height: 1rem;
}
.home{
   color:azure ;
   background-color:blueviolet
}
.title{
    position: absolute;
    top:50%;
    left:50%;
    transform:translate(-50%,-50%);
    color:blueviolet;
}
</style>


