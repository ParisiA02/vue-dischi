<template>
  <Container/>
</template>

<script>
import Container from './components/Container.vue'

export default {
  name: 'App',
  components: {
    Container
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
