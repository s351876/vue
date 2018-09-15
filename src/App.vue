<template>
  <div id="app">
    <my-form />
  </div>
</template>

<script>
import MyForm from './components/MyForm.vue'


export default {
  name: 'app',
  components: {
    MyForm
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 1200px;
  margin: 90px auto;
}
</style>
