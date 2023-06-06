<template>
  <div class="todo-progress">{{ progress }}</div>
</template>

<script>
export default {
  name: "TodoListProgress",
  props: {
    todos: {
      type: Array,
      required: true,
    }
  },
  computed: {
    completed() {
      return this.$props.todos.filter(todo => todo.checked).length
    },
    unfinished() {
      return this.$props.todos.length - this.completed;
    },
    progress() {
      if (this.completed) {
        return `${this.completed} TASKS COMPLETED OF ${this.$props.todos.length}. ${this.unfinished ? `ONLY ${this.unfinished} LEFT` : 'NO ONE LEFT'} `;
      }

      return `YOU NEED TO COMPLETE ${this.unfinished} TASKS.`
    }
  }
}
</script>

<style scoped>
.todo-progress {
    text-align: center;
    font-size: 16px;
    padding-block: 0.5em;
    margin-block: 0.5em;
    border-block: 1px solid #b6b6b6;
}
</style>
