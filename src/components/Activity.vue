<template>
  <div>
    <div> You may want to ... </div>
    <div> activité : {{data.activity}} </div>
    <div> type : {{data.type}} </div>
    <div> prix : {{translatePrice()}} </div>
    <div> nombre de participant(s) : {{data.participants}} </div>
  </div>
</template>
<script>
export default {
  name: "Activity",
  data() {
    return {

    };
  },
  methods: {
    translatePrice(){
      if (this.data.price < 0.1){
        return "€"
      }
      if (this.data.price < 0.4){
        return "€€"
      }
      if (this.data.price < 0.7){
        return "€€€"
      }
      return "€€€€"
    }
  },
  props: {
    data: {
      type : Object,
      required : true
    }
  },
};
</script>

<style scoped>
</style>