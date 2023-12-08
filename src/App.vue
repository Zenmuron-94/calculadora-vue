<script setup>
import { ref, watch } from 'vue';

const num1 = ref('');
const num2 = ref('');
const operacao = ref('+')
const resultado = ref(0);

const calculaResultado = () => {
  switch (operacao.value) {
    case '+':
      resultado.value = num1.value + num2.value;
      break;
    case '-':
      resultado.value = num1.value - num2.value;
      break;
    case '*':
      resultado.value = num1.value * num2.value;
      break;
    case '/':
      resultado.value = num1.value / num2.value;
      break;
    default:
      resultado.value = 0;
  }
};

watch([num1, num2, operacao], () => {
  calculaResultado();
});

</script>

<template>
<div class="container">
  <header class="text-center p-5 mb-4 mt-4 bg-light rounded-3">
    <h1>Calculadora Aritimetica</h1>

  </header>
  <form>
    <div class="row">
      <div class="col">
        <input v-model="num1" type="number" placeholder="0" class="form-control">
      </div>
      <div class="col">
        <input v-model="num2" type="number" placeholder="0" class="form-control">
      </div>
      <div class="col-md-2">
        <select v-model="operacao" class="form-control">
          <option value="+">Adição +</option>
          <option value="-">Subtração -</option>
          <option value="*">Multiplicação *</option>
          <option value="/">Divisão /</option>
        </select>
      </div>
    </div>
  </form>
  <h2 class="text-center p-5 mb-4 mt-4 bg-light rounded-3">Resultado:{{ resultado }}</h2>
</div>
</template>

<style scoped>

</style>
