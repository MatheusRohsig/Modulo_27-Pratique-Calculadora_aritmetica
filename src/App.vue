<script setup>
  import { reactive } from 'vue';
  
  const estado = reactive({
    primeiroNumero:'',
    segundoNumero: '',
    operacoes: {
      soma: (a, b) => a + b,
      subtracao: (a, b) => a - b,
      multiplicacao: (a, b) => a * b,
      divisao: (a, b) => a / b
    },
    resultado: 0,
  }); 

  const calcularResultado = () => {
    const { primeiroNumero, segundoNumero, operacaoMatematica } = estado;
    estado.resultado = estado.operacoes[operacaoMatematica](parseFloat(primeiroNumero), parseFloat(segundoNumero));
};

</script>

<template>
  <div class="container">
    <header class="text-center  p-5 mt-5 mb-5 bg-light rounded-3 ">
        <div class="row">
            <h1 class="text-uppercase">Calculadora Aritmética</h1>
        </div>
    </header>

    <form>

<div class="row bg-light rounded-3">
    <h4 class="text-center text-uppercase ">Escolha a operação aritmética</h4>
</div>

<div class="row mb-5 bg-light rounded-3">
    <select class="form-control" id="operacao" v-model="estado.operacaoMatematica" @change="calcularResultado">
        <option value="soma">Soma</option>
        <option value="subtracao">Subtração</option>
        <option value="multiplicacao">Multiplicação</option>
        <option value="divisao">Divisão</option>
    </select>
</div>

<div class="row bg-light rounded-3">
    <h4 class="text-center text-uppercase">Realize a sua operação aritmética</h4>
</div>

<div class="row mb-5">
    <div class="col-6">
        <input type="number" placeholder="Insira o primeiro numero" class="form-control"
            v-model="estado.primeiroNumero" @input="calcularResultado">
    </div>
    <div class="col-6">
        <input type="number" placeholder="Insira o segundo numero" class="form-control"
            v-model="estado.segundoNumero" @input="calcularResultado">
    </div>
</div>

<div class="row bg-light rounded-3">
    <h4 class="text-center text-uppercase">Resultado: {{ estado.resultado }}</h4>
</div>

</form>
  </div>
</template>

<style scoped>

</style>
