<template>
  <div style="width:100%; background:RGB(203,213,224);">
    <h3 class="pt-2">Test Function 2</h3>
    <div>{{formatDate}}</div>
    <div>{{formatThai}}</div>
    <div>{{formatDay}}</div>
    <div>{{formatQuarter}}</div>
    <div>{{formatUnix}}</div>
  </div>
</template>

<script>
import moment from "moment";

export default {
  name: "function1",
  props: {},

  data() {
    return {
      date: "2020-08-10T14:54:52+07:00",
    };
  },
  computed: {
    formatDate() {
      return moment(this.date).format("DD/MM/YYYY HH:mm");
    },
    formatThai() {
      return moment(this.date).add(543,'year').format("DD MMMM YYYY")
    },
    formatDay() {
      return moment(this.date).endOf('month').format("DD")
    },
        formatUnix() {
      return moment(this.date).format("X")
    },
    formatQuarter(){
      return moment(this.date).format("Q")
    }

  },
};
</script>

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
