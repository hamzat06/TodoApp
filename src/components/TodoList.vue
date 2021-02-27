<template>
  <div class="todo-list">
    <div v-for="todo in todos" :key="todo.id">
      <Todo :todo="todo" @del-todo="$emit('delTodo', todo.id)" />
    </div>
  </div>
</template>

<script>
import Todo from './Todo'

export default {
  name: 'TodoList',
  props: {
    todos: Array,
    todoBool: Boolean

  },
  components: {
    Todo
  }
}
</script>

<style>
.todo-list:last-child {
  border-bottom-left-radius: 5px;
  border-bottom-right-radius: 5px;
}
</style>
