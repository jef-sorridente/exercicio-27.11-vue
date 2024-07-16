<script setup>
import { reactive, ref } from 'vue';


const estado = reactive({
  num1: 0,
  num2: 0,
  selecao: ref('soma')
})

function capturaInput1(e) {
  estado.num1 = e.target.value
}
function capturaInput2(e) {
  estado.num2 = e.target.value
}


function calcula() {
  if (estado.selecao === "soma") {
    this.resultado = parseInt(estado.num1) + parseInt(estado.num2)

  } else if (estado.selecao === "subtracao") {
    this.resultado = parseInt(estado.num1) - parseInt(estado.num2)
  }
  else if (estado.selecao === "divisao") {
    this.resultado = parseInt(estado.num1) / parseInt(estado.num2)
  }
  else if (estado.selecao === "multiplicacao") {
    this.resultado = parseInt(estado.num1) * parseInt(estado.num2)
  }
  else {
    console.log("Nenhuma opção selecionada")
  }

  return this.resultado
}

</script>

<template>
  <div class="container rounded-5 p-3 mt-5 fs-4">
    <h1 class="text-center mb-5 mt-5">Calculadora Aritmética</h1>

    <label for="num1">Primeiro número:</label>
    <input id="num1" class="input-group" type="number" @keyup="capturaInput1">


    <label for="num2" class="mt-3">Segundo número:</label>
    <input id="num2" class="input-group " type="number" @keyup="capturaInput2">

    <div class="text-center mt-3 mb-5">
      <select class="form-select" v-model="estado.selecao">
        <option value="soma">Soma</option>
        <option value="subtracao">Subtração</option>
        <option value="divisao">Divisão</option>
        <option value="multiplicacao">Multiplicação</option>
      </select>
    </div>


    <p class="h2 text-center">Resultado:</p>
    <p class="h2 text-center">{{ calcula() }}</p>
  </div>
</template>

<style>
body,
.form-select,
.input-group {
  background-color: #1a1a1a;
  color: #e1e1e1;
}

.container {
  max-width: 600px;
  background-color: #242424;
  border: solid 2px #42b883
}
</style>
