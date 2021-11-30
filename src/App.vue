<template>
  <div class="contenitore">
    <header>
      <i class="fab fa-spotify"></i>
      <Selection @selection="selecting" />
    </header>
    <Container :selectedGenre="tempElement"/>
  </div>
</template>

<script>
import Container from './components/Container.vue'
import Selection from '@/components/Selection.vue'

export default {
  name: 'App',
  components: {
    Selection,
    Container
  },
  data(){
    return{
      tempElement:""
    }
  },
  methods:{
    selecting(text){
      this.tempElement = text;
      console.log(this.tempElement);
    }
  }
}
</script>

<style lang="scss">
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Arial, Helvetica, sans-serif;
  }

  body{
    height: 100vh;
  }

  header{
      width: 100%;
      height: 75px;
      background-color: #2E3A46;
      display: flex;
      justify-content: space-between;

      i{
        margin: 10px 20px;
        font-size: 50px;
        border-radius: 40px;
        color: #1ED760;
      }
    }
</style>
