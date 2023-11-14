<template>
  <div>
    <div> You may want to ... </div>
    <div> {{data.activity}} </div>
    <div> {{data.type}} </div>
    <div> {{translatePrice()}} </div>
    <div> {{data.participants}} </div>
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