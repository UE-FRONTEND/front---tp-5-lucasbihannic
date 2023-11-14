<template>
  <div>
    <label>type d'activité : </label>
    <select id="type-select" v-model="criteria.type">
      <option v-for="type in this.typeList" :value="type">{{type}}</option>
    </select>
    <label>nb person : </label>
    <select id="person-select" v-model="criteria.participants">
      <option v-for="personNumber in this.personNumberList"  :value="personNumber">{{personNumber}}</option>
    </select>
    <label>prix min</label>
    <input type="range" min="0" max="1" step="0.01" v-model="criteria.minprice"/>
    <label>prix max</label>
    <input type="range" min="0" max="1" step="0.01" v-model="criteria.maxprice"/>
    <button @click="sendCriteria">Rechercher</button>
  </div>
</template>
<script>
export default {
  name: "Criteria",
  data() {
    return {
      typeList: ["education", "recreational", "social", "diy", "charity", "cooking", "relaxation", "music", "busywork"],
      personNumberList: [1, 2, 3, 4],
      criteria : {
        type : "education",
        participants : 1,
        minprice : 0,
        maxprice : 1
      }
    };
  },
  methods: {
    sendCriteria(){
      this.$emit("sentCriteria", this.criteria)
    }
  },
  props: {

  },
};
</script>

<style scoped>
</style>