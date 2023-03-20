<template>
    <div>
        <div class="todoList" v-if="todos.length>0">
            <ToDoItem v-for="task in todos" :task="task" :key="task.id" @removeTask="$emit('removeTask', task)"/>
        </div>
        <div v-else class="empty">
            <h1>Список задач пуст</h1>
        </div>
    </div>
</template>

<script>
import ToDoItem from './ToDoItem.vue';

    export default {
        components: { ToDoItem },
        props: {
            todos: {
                id: Number,
                title: String,
            }
        },
}
</script>

<style scoped>
.todoList {
    display: flex;
    flex-flow: column nowrap;
    align-items: center;
    gap: 15px;
}
.empty {
    display: flex;
    justify-content: center;
}
</style>
