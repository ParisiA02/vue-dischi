<template>
  <div class="contenitore">
    <Selection @selection="selecting" />
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
</style>
