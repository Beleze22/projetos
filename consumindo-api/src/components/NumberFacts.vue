<template>
  <div>
    <input type="number" name="" id="" v-model="input" />
    <label for="tipos"></label>
    <select name="tipos" id="tipo">
      <option value="trivia">Trivia</option>
      <option value="math">Matemática</option>
      <option value="date">Data</option>
      <option value="year">Ano</option>
    </select>
    <button @click="getFact">Buscar</button>
    <p v-if="fact != null">{{ fact }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      input: null,
      fact: null,
    };
  },

  methods: {
    getFact() {
      let tipoSelecionado = document.querySelector("#tipo").value;
      let reqPath =
        "http://numbersapi.com/" + `${this.input}` + "/" + `${tipoSelecionado}`;
      axios.get(reqPath).then((response) => (this.fact = response.data));
    },
  },

  components: {},
};
</script>

<style></style>
