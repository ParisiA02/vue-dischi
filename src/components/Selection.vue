<template>
    <div class="select-container">
        <select name="select" class="select" v-model="selectedElement" @change="$emit('selection', selectedElement)">
          <option value="All">All</option>
          <option v-for="genre,i in genreArray" :key="i" :value="genre">{{genre}}</option>
        </select>
    </div>
</template>

<script>
  import axios from "axios";
  export default {
    name: 'Selection',
  
    data(){
        return{
          apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",  
          genreArray: [],
          selectedElement : "All"
        }
    },
    created(){
      this.getGenre();
    },
    methods: {
      getGenre(){
        axios
        .get(this.apiUrl)
        .then((result) => {
          let response = result.data.response;
          let tempArray = [];
          for(let i = 0; i < response.length; i++){
            tempArray.push(response[i].genre); 
            if(!(this.genreArray.includes(tempArray[i]))){
              this.genreArray.push(tempArray[i]);
            }
          }
          console.log(tempArray);
          console.log(this.genreArray);
        })
      }
    }
  }
</script>

<style lang="scss">
    .select-container{
      width: 200px;
      height: 50px;
      text-align: center;
      padding-top: 10px;
      margin-right: 20px;
    
      .select{
        text-align: center;
        display: block;
        font-size: 16px;
        font-family: sans-serif;
        font-weight: 700;
        color: #444;
        line-height: 1.3;
        padding: 10px;
        width: 100%;
        box-sizing: border-box;
        border: 1px solid #aaa;
        box-shadow: 0 1px 0 1px rgba(0,0,0,.04);
        border-radius: .5em;
        appearance: none;
        background-color: #fff;
      }
    }
</style>
