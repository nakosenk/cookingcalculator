<template>
  <div id="app">
    <img alt="Piggy Chef" src="./assets/piggy.png">
    <div>Multiplier: <input type="number" v-model.number="rootMultiplier" /></div>
    <PoundsAndOunces :rootMultiplier="rootMultiplier"/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import PoundsAndOunces from './components/PoundsAndOunces.vue';

@Component({
  components: {
    PoundsAndOunces,
  },
})
export default class App extends Vue {
  public data() {
    return {
      rootMultiplier: 2,
    };
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
