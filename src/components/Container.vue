<template>
  <div class="container">
    <header>
    </header>
    <div class="film-container">
      <Disc v-for="album,i in discArray" :key="i" :details="album"/>
    </div>
  </div>
</template>

<script>

import axios from "axios";
import Disc from '@/components/Disc.vue'

export default {
  name: 'Container',
  components:{
    Disc
  },
  data(){
    return{
      apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
      discArray: [],
    }
  },
  created(){
    console.log(this.getDisc());
  },
  methods: {
    getDisc(){
      axios
      .get(this.apiUrl)
      .then((result) => {
        this.discArray = result.data.response;
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  
  .container{
    width: 100%;
    background-color: #1E2D3B;

    header{
      width: 100%;
      height: 75px;
      background-color: #2E3A46;
    }

    .film-container{
      width: 60%;
      margin: 80px auto 0;
      display: flex;
      justify-content: space-between;
      flex-wrap: wrap;
    }
  }
</style>
