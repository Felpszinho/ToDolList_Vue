<script setup>
const porps =defineProps(['tarefas',])
</script>

<template>
    <ul class="done  list-group mt-4">
        <li class="list-group-item" v-for="tarefa in  porps.tarefas">
            <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada"
                :id="tarefa.titulo" type="checkbox">
            <label :class="{ done: tarefa.finalizada === true }" class="ms-3" :for="tarefa.titulo">
                {{ tarefa.titulo }}
            </label>
        </li>

    </ul>
</template>
<style scoped>

.done{
    text-decoration: line-through;
}
</style>