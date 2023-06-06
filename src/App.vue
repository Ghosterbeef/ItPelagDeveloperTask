<template>
  <main>
    <div class="todo-list-wrapper">
      <h1>THINGS TO DO</h1>
      <TodoListProgress v-if="todos.length" :todos="todos"/>
      <TodoListForm @submit="addTodo"/>
      <TodoList v-model:todos="todos"/>
    </div>
  </main>
</template>

<script>
import TodoListForm from "@/components/TodoListForm.vue";
import TodoList from "@/components/TodoList.vue";
import TodoListProgress from "@/components/TodoListProgress.vue";

const todosTemplate = [
  {
    id: 0,
    label: "Fix an ability to display all tasks",
    checked: false
  },
  {
    id: 1,
    label: "Fix a layout, checkboxes should be listed in a column",
    checked: false
  },
  {
    id: 2,
    label: "Fix an ability to add a new task",
    checked: false
  },
  {
    id: 3,
    label: "Fix an ability to toggle a task",
    checked: false
  },
  {
    id: 4,
    label: "Fix an ability to delete a task",
    checked: false
  },
  {
    id: 5,
    label: "Fix an ability to count completed tasks",
    checked: false
  }
];
export default {
  name: 'App',
  components: {TodoListProgress, TodoListForm, TodoList},
  data: () => ({
    todos: todosTemplate,
  }),
  methods: {
    addTodo(data) {
      this.todos.push({...data});
    }
  }
}

</script>

<style>

*, *::before, *::after {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: sans-serif;
    color: #343434;
    font-size: 16px;
    background-color: #e0e0e0;
}

main {
    display: grid;
    height: 100dvh;
    padding: 2em;
}

.todo-list-wrapper {
    margin: auto;
    padding: 2em;
    width: 100%;
    max-width: 720px;
    border-radius: 24px;
    background: #e0e0e0;
    box-shadow: 20px 20px 60px #bebebe,
    -20px -20px 60px #ffffff;
}

h1 {
    text-align: center;
}
</style>
