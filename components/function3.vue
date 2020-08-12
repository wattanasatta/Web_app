<template>
  <div style="width:100%; background:RGB(203,213,224);">
    <h3 class="pt-2">Test Function 3</h3>
    <div>case1: {{a1}}</div>
    <div>{{findMax2(a1) ?findMax2(a1) : 'null' }}</div>
    <div>case2: {{a2}}</div>
    <div>{{findMax2(a2)}}</div>
    <div>case3: {{a3}}</div>
    <div>{{findMax2(a3)}}</div>
  </div>
</template>

<script>
import axios from "@nuxtjs/axios";

export default {
  name: "function1",
  props: {},

  data() {
    return {
      a1: [],
      a2: [1],
      a3: [1, 2, 5, 4, 5, 10]
    };
  },
  methods: {
    findMax2(array) {
      var sorted = [];
      if (!array) return null;
      else if (array.length == 1) return array[0];
      // array.sort((a, b) => a - b);
      else {
        var maxArray = [];
        // var index = array.length;
        var max = array[0];
        maxArray.push(max);
        for (let index = 0; index < array.length; index++) {
          const element = array[index];
          if (element > max) {
            max = element;
            maxArray.push(max);
          }
        }
        // var max2 = array[index - 2];

        return maxArray[maxArray.length - 2];
      }
    }
  }
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
