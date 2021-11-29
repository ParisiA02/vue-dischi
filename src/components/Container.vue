<template>
  <div class="container">
    <header>
      <i class="fab fa-spotify"></i>
    </header>
    <Selection @selection="selecting()" />
    <div class="film-container">
      <Disc v-for="album,i in discArray" :key="i" :details="album"/>
    </div>
  </div>
</template>

<script>

import axios from "axios";
import Disc from '@/components/Disc.vue'
import Selection from '@/components/Selection.vue'

export default {
  name: 'Container',
  components:{
    Selection,
    Disc
  },
  data(){
    return{
      apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
      discArray: [],
      displayElement:""
    }
  },
  created(){
    this.getDisc();
  },
  computed:{
    //filteredList(){
    //   return this.discArray.filter((item) =>{
    //       return item.genre === 
    //
    //}

  },
  methods: {
    getDisc(){
      axios
      .get(this.apiUrl)
      .then((result) => {
        this.discArray = result.data.response;
      })
    },
    selecting(text){
      this.displayElement = text;
      console.log(this.displayElement);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  
  .container{
    width: 100%;
    min-height: 100vh;
    background-color: #1E2D3B;

    header{
      width: 100%;
      height: 75px;
      background-color: #2E3A46;
      
      i{
        margin: 10px 20px;
        font-size: 50px;
        border-radius: 40px;
        background-color: black;
        color: #1ED760;
      }
    }

    .film-container{
      width: 60%;
      margin: 20px auto 0;
      display: flex;
      justify-content: space-between;
      flex-wrap: wrap;
    }
  }
</style>
