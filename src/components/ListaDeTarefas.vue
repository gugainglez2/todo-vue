<script setup>
    const props = defineProps(['tarefas', 'filtro']);
</script>
<template>
    <ul v-if="props.tarefas.length > 0" class="list-group mt-4">
        <li class="list-group-item" v-for="tarefa in props.tarefas" :key="tarefa.titulo">
            <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada"
                :id="tarefa.titulo" type="checkbox">
            <label :class="{ done: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">
                {{ tarefa.titulo }}
            </label>
        </li>
    </ul>

    <p v-else class="mt-4">
        <span v-if="props.filtro === 'pendentes'">Não há tarefas pendentes.</span>
        <span v-else-if="props.filtro === 'finalizadas'">Não há tarefas finalizadas.</span>
        <span v-else>Você não possui tarefas cadastradas.</span>
    </p>
</template>
<style scoped>
.done {
    text-decoration: line-through;
}
</style>