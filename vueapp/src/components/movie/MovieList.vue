<template>
 <div>
      <ul class="movie-list">
          <li @click="goDetail(movie.id)" v-for="movie in moveList" :key='movie.id' class="movie">
              <div class="movie-img">
                  <img :src="movie.img" alt="">
              </div>
              <div class="movie-info">
                  <p class="movie-name">{{movie.nm}}</p>
                  <p>{{movie.ver}}</p>
                  <p>主演：{{movie.star}}</p>
                  <p>{{movie.rt}}</p>
              </div>
          </li>
     </ul>
     <div class="movie-loading" v-show="loadingShow">
         <img src="../../assets/img/loading.gif" alt="">
     </div>
     <div v-show="tip" class="tip">
         <h4>已经到底啦</h4>
     </div>
</div>
</template>
<script>
import Axios from "axios";
export default {
  data(){
      return {
          moveList:[],
          loadingShow:true,
          tip:false
      };
  },
  mounted(){
      console.log('111');
      this.loadData();
      console.log('222');
      window.onscroll=()=>{
          console.log('333');
        let clientHeight=document.documentElement.clientHeight;
        let scrollTop=Math.ceil(document.documentElement.scrollTop || document.body.scrollTop); 
        let scrollHeight=document.documentElement.scrollHeight;
        console.log(clientHeight,scrollTop,scrollHeight);
        if(clientHeight+scrollTop==scrollHeight){
            console.log('到底了');
            this.loadingShow=true;
            if(!this.tip){
                this.loadData();
            }
            else{
                this.loadingShow=false;
            }
        }
      };
     
  },
  methods:{
      loadData(){
      let url1=API_PROXY+"http://m.maoyan.com/movie/list.json?type=hot&limit=10&offset=" + this.moveList.length;
      let url2='../../static/data/moviedata.json'
    Axios.get(url2)
    .then(res=>{
        console.log(res);
         let list=res.data.data.movies;
         let data=list.slice(this.moveList.length,
         this.moveList.length+10);
         this.loadingShow=false;
        if(data.length<10){
            this.tip=true;
        }
        console.log('444');
        this.moveList=this.moveList.concat(data);
    })
    .catch(()=>{});
      },
      goDetail(movieId){
          this.$router.push('/movieDetail/'+movieId);
      }
  }
}
</script>
<style scoped>
.movie{
    display: flex;
    padding:0.2rem;
    border-bottom:1px solid #ccc;
}
.movie-img{
    flex-grow:1;
    margin-right:0.2rem;
    width:0;   
}
.movie-img img{
    width:100%;
}
.movie-info{
    flex-grow:2;
    width:0;
}
.movie-list{
    margin:1rem 0;
}
.movie-name{
    font-weight:bolder;
}
.movie-loading{
    text-align:center;
}
.tip{
    text-align:center;
}
</style>





