<script setup>
import { defineProps, defineEmits } from 'vue';

let props = defineProps(['operacao', 'primeiroNumero', 'segundoNumero']);
let emits = defineEmits(['editaPrimeiroNumero', 'editaSegundoNumero', 'calcularResultado']);

const calcularEmitindoEvento = () => {
    emits.calcularResultado();
};
</script>

<template>
    <form @submit.prevent="calcularEmitindoEvento">
        <div class="row">
            <div class="col">
                <input v-model="props.primeiroNumero" @input="editaPrimeiroNumero" required type="text" placeholder="Digite aqui o primeiro número" class="form-control text-center">
            </div>
            <div class="col-md-1">
                <select v-model="props.operacao" class="form-control text-center">
                    <option value="soma">+</option>
                    <option value="subtracao">-</option>
                    <option value="multiplicacao">x</option>
                    <option value="divisao">/</option>
                </select>
            </div>
            <div class="col">
                <input v-model="props.segundoNumero" @input="editaSegundoNumero" required type="text" placeholder="Digite aqui o segundo número" class="form-control text-center">
            </div>
        </div>
    </form>
</template>