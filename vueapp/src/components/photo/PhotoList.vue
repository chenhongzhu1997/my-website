<template>
  <ul class="photo clearfix">
      <li v-for='(photo,index) in photoList' :key='index' class="tabs">
          <router-link :to="'/photo/photoDetail/'+index">
              <img :src="photo.src" alt="">
          </router-link>
          
      </li>
  </ul>
</template>
<script>
import Axios from 'axios';
export default {
    data(){
        return {
            photoList:[]
        };
    },
    mounted(){
        Axios.get("/static/data/photodata.json")
        .then(res => {
            console.log(res);
            this.photoList=res.data.photoData;
            this.$store.dispatch('setPhotoList',res.data.photoData);
        })
        .catch(err=>{});
       
    }
};
</script>
<style scoped>
@import url("../../assets/css/common.css");
.photo{
    margin:1rem 0;
}
.tabs{
    float:left;
    width:50%;

}
.tabs img{
    width:100%;
}
</style>

