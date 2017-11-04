<template>
<div class="temp">
     {{msg}}
     <router-view></router-view>
</div>
</template>
<script>
export default{
    name:"test",
    data(){
        return {
            msg:"hahaha"
        }
    }
}
</script>
<style scope>
  /* .temp{
      background:#f00;
  } */
</style>