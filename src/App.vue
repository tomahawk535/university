<template>
  <div id="app">
    <SearchUniversity></SearchUniversity>
  </div>
</template>

<script>
import SearchUniversity from './components/SearchUniversity.vue'

export default {
  name: 'App',
  components: {
    SearchUniversity
  },

}
</script>

<style>
body {
  background-color: antiquewhite;
}
#app {
  background-color: antiquewhite;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding-top: 60px;
}
</style>
