<template>
  <div id="app">
    <div id="nav">
      <div class="container" style="background:lightslategrey; height:100px;">
        <h1
          class="title"
          style="color:white;font-weight:bold;justify-content: center;"
        >Test Frontend</h1>
      </div>
      <!-- <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>-->
    </div>
    <div class="container">
      <b-tabs content-class="mt-3" align="center" style="min-width:100%">
        <b-tab class="tab pb-3" title="home" active style="align-content:center">
          <formValidate/>
        </b-tab>
        <b-tab class="tab pb-3" title="pokemon" lazy>
            <pokemon/>
        </b-tab>
        <b-tab class="tab pb-3" title="function1"><function1/></b-tab>
        <b-tab class="tab pb-3" title="function2"><function2/></b-tab>
        <b-tab class="tab pb-3" title="function3"><function3/></b-tab>
      </b-tabs>
      <!-- <table style="margin:auto;width:60%" >
        <thead >
          <th class="tab pb-3" @click="tab = 'home'">home</th>
          <th class="tab pb-3" @click="tab = 'pokemon'">pokemon</th>
          <th class="tab pb-3" @click="tab = 'function1'">Function 1</th>
          <th class="tab pb-3" @click="tab = 'function2'">Function 2</th>
          <th class="tab pb-3" @click="tab = 'function3'">Function 3</th>
        </thead>
        <tbody>
          <tr>
            <td colspan="5">
              
            </td>
          </tr>
        </tbody>
      </table>-->
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import formValidate from "@/components/formValidate.vue";
import pokemon from "@/components/pokemon.vue";
import function1 from "@/components/function1.vue";
import function2 from "@/components/function2.vue";
import function3 from "@/components/function3.vue";
export default {
  name: "Home",
  components: {
    formValidate,
    pokemon,
    function1,
    function2,
    function3,
  },
  data() {
    return {
      tab: "home"
    };
  }
};
</script>

<style>
.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  /* font-size: 20px; */
  color: #35495e;
  letter-spacing: 1px;
}

.container {
  /* margin: 0 auto; */
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  border-radius: 10px;
}
th {
  padding: 2rem;
}
</style>
