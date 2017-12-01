<template>
<div>
    <common-header>
        <span slot="title">Movie</span>
    </common-header>
    <router-view></router-view>
    <common-footer></common-footer>
</div>
  
</template>
<script>
import commonHeader from '../common/Header'
import commonFooter from '../common/Footer'
export default {
  components:{
      commonHeader,
      commonFooter
  }
}
</script>
<style scoped>

</style>

