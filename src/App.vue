<template>
  <div style="text-align: left">
    <button @click="getDataFromAPI">DO</button>
  </div>
</template>

<script>

import axios from "axios";

export default {
  name: 'App',
  data () {
    return {
      data: null
    }
  },
  methods : {
    getDataFromAPI(){
      axios
          .get('https://www.boredapi.com/api/activity')
          .then(response => {this.data = response
            console.log(this.data)})
    }
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
</style>
