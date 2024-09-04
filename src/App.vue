<script setup>
  import { reactive } from 'vue';

  const estado = reactive({
    operador: 'adicao',
    campoA: 0,
    campoB: 0,
    resultado: 0
  })

  const operacao = () => {
    const {operador, campoA, campoB} = estado
    const numA = parseFloat(campoA)
    const numB = parseFloat(campoB)

    switch(operador){
      case 'subtracao':
        estado.resultado = numA - numB
        return estado.resultado

      case 'divisao':
        estado.resultado = numA / numB
        return estado.resultado

      case 'multiplicacao':
        estado.resultado = numA * numB
        return estado.resultado
      
      default:
        estado.resultado = numB + numB
        return estado.resultado
    }
  }
</script>

<template>
  <body class="container">
    <header class="p-5 mb-4 mt-4 bg-primary rounded-3 text-center">
      <h1 class="text-white">Calculadora com vueJS</h1>
    </header>
    <form class="d-flex justify-content-center align-items-center flex-column">
      <input @change="event => estado.campoA = event.target.value" type="number" class="mx-auto mb-3" required >
      <select @change="event => estado.operador = event.target.value" class="mb-3">
        <option value="adicao" selected>+</option>
        <option value="subtracao">-</option>
        <option value="divisao">÷</option>
        <option value="multiplicacao">x</option>
      </select>
      <input @change="event => estado.campoB = event.target.value" type="number" class="mx-auto">
      <span> {{ operacao() }}</span>
    </form>
  </body>
</template>

<style scoped>

</style>
