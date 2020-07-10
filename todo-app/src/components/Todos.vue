<template>
  <ul>
    <li v-bind:key="todo.id" v-for="todo in todos" class="flex">
      <Todo v-bind:todo="todo" v-on:delete-todo="$emit('delete-todo', todo.id)" />
    </li>
  </ul>
</template>


<script>
import Todo from "./Todo";

export default {
  name: "Todos",
  components: { Todo },
  props: ["todos"]
};
</script>

<style>
.flex {
  display: flex;
}
</style>
