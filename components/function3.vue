<template>
  <div style="width:100%; background:RGB(203,213,224);">
    <h3 class="pt-2">Test Function 3</h3>
    <div>case1: {{a1}}</div>
    <div>{{findMax2(a1) }}</div>
    <div>case2: {{a2}}</div>
    <div>{{findMax2(a2)}}</div>
    <div>case3: {{a3}}</div>
    <div>{{findMax2(a3)}}</div>
    <div>case4: {{a4}}</div>
    <div>{{findMax2(a4)}}</div>
    <div>case5: {{a5}}</div>
    <div>{{findMax2(a5)}}</div>
    <div>case6: {{a6}}</div>
    <div>{{findMax2(a6)}}</div>
    <div>case7: {{a7}}</div>
    <div>{{findMax2(a7)}}</div>
    <div>case8: {{a8}}</div>
    <div>{{findMax2(a8)}}</div>
    <div>case9: {{a9}}</div>
    <div>{{findMax2(a9)}}</div>
    <div>case10: {{a10}}</div>
    <div>{{findMax2(a10)}}</div>
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
      a3: [1,2,3], // 2
      a4: [1,1], // 1
      a5: [1,2,3,4,5,6], // 5
      a6: [1,5,3,2,5,10], // 5
      a7: [100,5,3,2,99], // 99
      a8: [35,5,3,2,5,100], // 35
      a9: [1,5,101,2,5,10], // 10
      a10: [10,10,9], // 9
    };
  },
  methods: {
    findMax2(array) {
      var sorted = array.slice(0)
      if (array.length < 1) return 'null';
      else if (array.length == 1) return array[0];
      else {
        sorted.sort((a, b) => a - b)
        var maxArray = [];
        var max = sorted[0];
        maxArray.push(max);
        for (let index = 1; index < sorted.length; index++) {
          const element = sorted[index];
          if (element > max) {
            max = element;
            maxArray.push(max);
          }
        }
        return maxArray.length > 1 ? maxArray[maxArray.length - 2] : maxArray[0];
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
