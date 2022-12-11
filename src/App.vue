<template>
<h1>WordCounter</h1>
  <Editor />

</template>

<script>
import Editor from "./components/Editor.vue";
export default {
  name: 'App',
  data() {
    return { 
      
    }
  },
  components: {Editor},
  methods: {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body{
  margin: 0;
  padding: 0;
}
h1{
  text-align: center;
}
</style>
