<template>
  <div style="width:100%; background:RGB(203,213,224);align-content:center">
    <h3 class="pt-2">Test fetch API</h3>
    <table>
      <tbody>
        <tr v-for="i in 18" :key="i">
          <td v-for="j in 6" :key="j" class="p-3">
            <b-card
              v-if="((j-1)+((i-1)*6)) <= 103"
              style="min-width: 120px;min-height:125px"
              img-top
            >
              <div v-if="pokemons[(j-1)+((i-1)*6)]">
                <div v-lazy-container="{ selector: 'img' }">
                  <img width="60px" :data-src="pokemons[(j-1)+((i-1)*6)].url" data-loading />
                </div>
                <b-card-body class="pt-0">{{pokemons[(j-1)+((i-1)*6)].name}}</b-card-body>
              </div>
            </b-card>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from "@nuxtjs/axios";

export default {
  name: "pokemon",
  props: {},
  data() {
    return {
      count: 1,
      loadData: true,
      index: 0,
      rows: [],
      pokemons: []
    };
  },
  methods: {},
  mounted() {
    this.pokemons = [];
    this.index = 0;
    this.$nextTick(() => {
      for (let index = 0; index < 104; index++) {
        this.$axios
          .$get("https://pokeapi.co/api/v2/pokemon/" + (index + 1))
          .then(data => {
            if (data) {
              var poke = {
                name: "",
                url: ""
              };
              poke.name = data.name;
              poke.url = data.sprites.front_default;
              this.pokemons.push(poke);
            }
          });
      }
      //   // this.fetchSomething();
      //   // setTimeout(() => this.$nuxt.$loading.finish(), 2000)
      // console.log("mounted -> this.pokemons", Array.isArray(this.pokemons));
    }, 2000);
    console.log("mounted -> this.pokemons", this.pokemons[0]);
  },
  watch: {
    pokemons() {}
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
table{
  margin-left: 100px;
  margin-right: 0;
  align-self: center;
}
.primary {
  color: #42b983;
}
.card-body {
  padding: 0px;
}
</style>
