<script setup>
const props=defineProps(['tarefaspendentes'])
</script>
<template>
    <header>
        <h1>Minhas Tarefas</h1>
        <p>Você possui {{ props.tarefaspendentes }} tarefas pendentes</p>
    </header>
</template>