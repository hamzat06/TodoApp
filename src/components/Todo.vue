<template>
  <div class="todo">
    <p :class="{'is-completed': todo.completed}">
      <input type="checkbox" name="title" @change="todo.completed = !todo.completed">
      {{ todo.title }}
      </p>
      <button class="btn-custom" @click="$emit('del-todo', todo.id)">x</button>
  </div>
</template>

<script>
export default {
  name: 'Todo',
  props: [
    'todo'
  ],
  methods: {
  }
}
</script>

<style>
.todo {
  border-bottom: 1px solid purple;
  padding: 1.3rem;
  line-height: 1px;
  display: flex;
  justify-content: space-between;
}

.todo p {
  margin: 0;
}

.is-completed {
  text-decoration: line-through;
}

.btn-custom {
  margin: 0;
  height: 20px;
  padding: 0;
  width: 20px;
  padding-bottom: 3px;
  border-radius: 50%;
  border: none;
  color: red;
  font-size: 20px;
  margin-top: -5px;
}
</style>
