<template>
  <div class="no-todo">
    <p>You have no to-do item</p>
    <p>Or App is loading todos</p>
  </div>
</template>

<script>
export default {
  name: 'NoTodo'
}
</script>

<style>
.no-todo {
  color: purple;
  font-weight: 700;
  text-align: center;
  padding-bottom: 1rem;
}

.no-todo p {
  margin: 0;
}
</style>
