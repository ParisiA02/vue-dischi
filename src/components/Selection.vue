<template>
    <div class="select-container">
        <select name="select" class="select" @change="select(event)">
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
      },
      select(event){
        this.$emit('selection', event);
        console.log(this.$emit('selection', event.genreArray));
      }
    }
  }
</script>

<style lang="scss">
    .select-container{
      width: 60%;
      height: 50px;
      text-align: center;
      margin: 0 auto;
    
      .select{
        text-align: center;
          display: block;
          font-size: 16px;
          font-family: sans-serif;
          font-weight: 700;
          color: #444;
          line-height: 1.3;
          padding: 10px;
          width: 20%;
          max-width: 20%; /* useful when width is set to anything other than 100% */
          box-sizing: border-box;
          margin-top: 20px;
          border: 1px solid #aaa;
          box-shadow: 0 1px 0 1px rgba(0,0,0,.04);
          border-radius: .5em;
          -moz-appearance: none;
          -webkit-appearance: none;
          appearance: none;
  background-color: #fff;
      }
    }
</style>
