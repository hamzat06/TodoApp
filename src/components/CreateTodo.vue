<template>
  <div class="create-todo">
    <form @submit.prevent>
      <input type="text" id="title" v-model="title" placeholder="Add todo...">
      <button @click="addTodo">+</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'CreateTodo',
  data () {
    return {
      title: ''
    }
  },
  methods: {
    addTodo (newTodo) {
      newTodo = {
        title: this.title,
        completed: false
      }
      this.$emit('addTodo', newTodo)
    }
  }
}
</script>

<style>
.create-todo input {
  width: 25.5rem;
  height: 3rem;
  margin-left: 1.3rem;
  border-left: none;
  border-top: none;
  border-right: none;
  border-bottom: 1px solid purple;
}

.create-todo button {
  border: none;
  background: inherit;
  font-size: 30px;
  color: purple;
}
</style>
