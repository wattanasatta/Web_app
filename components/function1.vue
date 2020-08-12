<template>
  <div style="width:100%; background:RGB(203,213,224);align-content:center">
    <h3 class="pt-2">Test Function 1</h3>
    <div v-for="json in jsonData" :key="json.id">
      <div v-if="!json.is_editable_price">
        name: {{json.name}}, totalSubProductWeight: {{getWeight(json.products)}}
      </div>
      
    </div>
  </div>
</template>

<script>

export default {
  name: "function1",
  props: {},

  data() {
    return {
      jsonData: []
    };
  },
  methods: {
    getWeight(product){
      var weight = 0
      product.forEach(element => {
        weight += element.weight
      });

      return weight
    }
  },
  mounted() {

    let dataFile = require("../assets/data.json");
    this.jsonData = dataFile.data;
  },
  watch: {}
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.error {
  size: 8px;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
.primary {
  color: #42b983;
}
.card-body {
  padding: 0px;
}
</style>
