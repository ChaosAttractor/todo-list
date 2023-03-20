<template>
  <div>
    <div class="todoform">
      <input type="text" class="input" placeholder="Введите название задачи и нажмите Enter" v-model="todoinput" @keyup.enter="addToDo">
      <button @click="addToDo" class="btn">Добавить</button>
    </div>
    <ToDoList :todos="todos" @removeTask="remove"/>
  </div>
</template>

<script>
import ToDoList from './components/ToDoList.vue';

  export default {
    components: { ToDoList },
    data() {
      return {
        todos: [],
        todoinput: '',
      }
    },
    methods: {
      addToDo() {
        if (this.todoinput.length > 0) {
          let uniqueId = Math.floor(Math.random() * (100 - 1) + 1)
          this.todos.push({id: uniqueId, title: this.todoinput, date: new Date().toLocaleDateString("en-GB")})
        }
      },
      remove(task) {
        this.todos = this.todos.filter(t => t.id !== task.id)
      }
    },
}
</script>

<style scoped>
* {
  font-family: 'Roboto', sans-serif;
}
.todoform {
  display: flex;
  justify-content: center;
  margin: 30px 0;
}
.btn {
  user-select: none;
  cursor: pointer;
  border: 1px solid var(--main-btn-color);
  border-radius: 10px;
  background: none;
  padding: 5px;
  margin-left: 5px;
  font-size: 1.1em;
}
.btn:active {
  border: 1px solid var(--active-btn-color);
}
.input {
  border: 1px solid var(--main-btn-color);
  border-radius: 10px;
  background: none;
  padding: 10px 5px;
  width: 400px;
  font-size: 1.2em;
}
.input:focus {
  outline: 0;
  border: 1px solid var(--active-btn-color); /*не работает*/
}
</style>