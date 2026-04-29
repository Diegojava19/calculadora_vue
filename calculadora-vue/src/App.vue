<script setup>
import { ref, computed } from 'vue'

const num1 = ref(0)
const num2 = ref(0)
const operacao = ref('+')

const resultado = computed(() => {
  switch (operacao.value) {
    case '+': return num1.value + num2.value
    case '-': return num1.value - num2.value
    case '*': return num1.value * num2.value
    case '/': return num2.value !== 0 ? num1.value / num2.value : 'Erro'
    default: return 0
  }
})
</script>

<template>
  <div class="container">
    <h1>Calculadora</h1>

    <input type="number" v-model.number="num1" />

    <select v-model="operacao">
      <option value="+">Soma</option>
      <option value="-">Subtração</option>
      <option value="*">Multiplicação</option>
      <option value="/">Divisão</option>
    </select>

    <input type="number" v-model.number="num2" />

    <h2>Resultado: {{ resultado }}</h2>
  </div>
</template>

<style>
.container {
  max-width: 400px;
  margin: 100px auto;
  text-align: center;
}

input, select {
  display: block;
  width: 100%;
  margin: 10px 0;
  padding: 8px;
}
</style>