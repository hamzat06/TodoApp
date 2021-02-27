<template>
  <div class="container todo-app">
    <Header />
    <CreateTodo @addTodo="createTodo" />
    <TodoList :todos="todos" :todoBool="todoBool" v-if="todoBool" @delTodo="deleteTodo" />
    <NoTodo :todoBool="todobool" v-else />
  </div>
</template>

<script>
import axios from 'axios'
import Header from './layout/Header'
import TodoList from './TodoList'
import NoTodo from './NoTodo'
import CreateTodo from './CreateTodo.vue'

export default {
  name: 'TodoApp',
  data () {
    return {
      api: 'http://localhost:3000/todos/',
      todos: [],
      title: '',
      todoBool: false
    }
  },
  components: {
    Header,
    TodoList,
    NoTodo,
    CreateTodo
  },
  async mounted () {
    const {data} = await axios.get(this.api)
    this.todos = data
    this.todoBoolean()
  },
  methods: {
    todoBoolean () {
      if (this.todos.length !== 0) {
        this.todoBool = true
      } else {
        this.todoBool = false
      }
    },
    async deleteTodo (id) {
      await axios.delete(this.api + id).then(() => {
        this.todos = axios.get(this.api)
      })
    },
    async createTodo (newTodo) {
      const {data} = await axios.post(this.api, {
        id: this.todos.length + 1,
        title: newTodo.title,
        completed: newTodo.completed
      })
      this.todos = [...this.todos, data]
    }
  }
}
</script>

<style>
  .todo-app {
    width: 30rem;
    padding: 0;
    margin: 0 auto;
    margin-top: 1rem;
    min-height: 5rem;
    box-shadow: 2px 2px 20px black;
    border-radius: 5px;
  }
</style>
