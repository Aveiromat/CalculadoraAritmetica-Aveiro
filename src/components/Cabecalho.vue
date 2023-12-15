<script setup>
    const props = defineProps(['tarefaPendentes'])
</script>

<template>
    <header class="p-5 mb-4 mt-4 bg-light rounded-3 d-flex justify-content-center">
        <h1>
            O resultado é: {{ props.tarefaPendentes }}
        </h1> 
    </header>
</template>
