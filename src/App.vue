<template>
  <div id="app">
    <v-header></v-header>
    <div class="allcontent">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
  import Header from './components/header.vue'
  export default {
    name: 'app',
    components: {
      "v-header": Header,
    }
  }
</script>

<style>
  *{
    margin: 0;
    padding: 0;
  }
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    /*width: 100%;
    height: 100%;
    position: relative;*/
    z-index: -1000;
  }
  .allcontent{
    width:1000px;
    margin: 0 auto;
    border-top: 1px solid #dbe2e8;
    border-left: 1px solid #dbe2e8;
    border-right: 1px solid #dbe2e8;
    box-shadow: 0 1px 2px rgba(46,61,73,.08);
    border-radius: 4px;
    padding:10px ;
    background: #fff;
    /*position: relative;*/
    z-index: -500;
    margin-top: 70px;
  }
</style>
