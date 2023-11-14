<template>
  <div style="text-align: left">
      <criteria @sentCriteria="getDataFromAPI"></criteria>
    <activity v-if="this.data && !this.data.error" :data="this.data"></activity>
    <label v-if="this.data && this.data.error"> Aucune activité trouvé pour ces paramètres</label>
  </div>
</template>

<script>

import axios from "axios";
import Activity from "./components/Activity.vue";
import Criteria from "./components/Criteria.vue";

export default {
  name: 'App',
  components: {
    Activity,
    Criteria
  },
  data () {
    return {
      data: null
    }
  },
  methods : {
    getDataFromAPI(criteria){
      console.log(criteria)
      if (criteria.minprice <= criteria.maxprice){
        axios
            .get('https://www.boredapi.com/api/activity', {params : criteria})
            .then(response => {this.data = response.data; console.log(this.data)})

      }
      else{
        alert("Prix min superieur au prix max !");
      }
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
