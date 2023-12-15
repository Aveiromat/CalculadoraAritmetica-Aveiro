<script setup>
import { reactive, defineProps } from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';

let estado = reactive({
  primeiroNumero: '',
  segundoNumero: '',
  operacao: 'soma',
  resultado: null,
});

const calcularResultado = () => {
  let num1 = parseFloat(estado.primeiroNumero);
  let num2 = parseFloat(estado.segundoNumero);

  switch (estado.operacao) {
    case 'soma':
      estado.resultado = num1 + num2;
      break;
    case 'subtracao':
      estado.resultado = num1 - num2;
      break;
    case 'multiplicacao':
      estado.resultado = num1 * num2;
      break;
    case 'divisao':
      estado.resultado = num1 / num2;
      break;
    default:
      estado.resultado = null;
  }
};
</script>

<template>
  <div class="container d-flex flex-column vh-100 justify-content-center col-12">
    <div>
      <h1 class="col-12 d-flex justify-content-center pb-3">Calculadora Aritmética</h1>
      <Formulario
        :operacao="estado.operacao"
        :primeiroNumero="estado.primeiroNumero"
        :segundoNumero="estado.segundoNumero"
        :editaPrimeiroNumero="evento => (estado.primeiroNumero = evento)"
        :editaSegundoNumero="evento => (estado.segundoNumero = evento)"
        :calcularResultado="calcularResultado"
      />
      <Cabecalho :resultado="estado.resultado" />
      <span>{{ resultado }}</span>
    </div>
  </div>
</template>
