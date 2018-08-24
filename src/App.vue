<template>
  <div id="app">
    <img src="./assets/logo.png">
    <!--<router-view/>-->
    <ListView :msg= "title" @myMsg= "getData"></ListView>
  </div>
</template>

<script>
import ListView from './components/list';

export default {
  name: 'App',
  components: { //註冊
    ListView
  },
  data(){
    return {
      title: 'ToDo 可愛'
    }
  },
  methods: {
    getData(msg) {
      console.log('ok');
      this.title= msg;
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
