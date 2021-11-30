<template>
  <div class="container">
    <div class="film-container">
      <Disc v-for="album,i in filtered" :key="i" :details="album"/>
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
  props: {
    selectedGenre: String
  },
  created(){
    this.getDisc();
  },
  computed:{
    filtered() {
      if (this.selectedGenre == "All") {
        return this.discArray;
      }
      // il filter su discArray con displayElement
      return this.discArray.filter((item) => {
          return item.genre.includes(this.selectedGenre);
      });
    },
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
    min-height: calc(100vh - 75px);
    background-color: #1E2D3B;

    .film-container{
      width: 60%;
      padding-top: 20px;
      margin: 0 auto;
      display: flex;
      justify-content: space-between;
      flex-wrap: wrap;
    }
  }
</style>
