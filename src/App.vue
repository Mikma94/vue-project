<template>
  <div id="app">
    <mf-bit-coins-component></mf-bit-coins-component>
  </div>
</template>

<script>
import BitCoinsComponent  from '/components/BitCoinsComponent';
import 'vue-select/dist/vue-select.css';
export default {
  name: 'BitCoinsEquivalences',
  components: {
    'mf-bit-coins-component': BitCoinsComponent,
  },
  data() {
    return {
      dummy: []
    }
  }
};
</script>

<style>
#app {
  font-family: Arial, Helvetica, sans-serif;

}
* {
  box-sizing: border-box;
}
</style>

