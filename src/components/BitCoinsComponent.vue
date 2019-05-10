<template>
  <div>
    <h1>Equivalencias en BitCoins</h1>
    <label>Ultima actualización:</label>
    <input v-model="apiResponse.time.updated" class="form-label">
    <br>
    <label>Selecciona tipo de moneda</label>
    <v-select :options="options" @input="onCoinSelected"></v-select>
    <br>
    <label v-if="bitCoinValue">Valor en BitCoins</label>
    <input v-if="bitCoinValue" v-model="bitCoinValue" class="form-label">
    <br>
    <button class="update-button" type="button" @click="update()">
      Actualizar
    </button>
  </div>
</template>

<script>
import axios from 'axios';
import vSelect from 'vue-select';
export default {
  components: {
    'v-select': vSelect
  },
  data() {
    return {
      apiResponse: null,
      bitCoinValue: null,
      options: ['USD', 'GBP', 'EUR']
    }
  },
  mounted() {
    axios.get('https://api.coindesk.com/v1/bpi/currentprice.json')
      .then(response => (this.apiResponse = response.data))
  },
  methods: {
    onCoinSelected: function(value) {
      this.bitCoinValue = this.apiResponse.bpi[value].rate;
    },
    update: function() {
      document.location.reload();
    }
  }
}
</script>

<style>

@import "vue-select/src/scss/vue-select.scss";

.form-label {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

.update-button {
  width: 50%;
  background-color: rgb(48, 121, 216);
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
</style>
