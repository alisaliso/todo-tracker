<template>
  <input
    type="text"
    v-model="title"
    name="title"
    class="input nes-input"
    placeholder="Add todo..."
    v-on:keyup.enter="addTodo"
  />
</template>


<script>
export default {
  name: "AddTodo",
  data() {
    return { title: "" };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const newTodo = {
        id: Math.random(),
        title: this.title,
        checked: false
      };

      this.$emit("add-todo", newTodo);
      this.title = "";
    }
  }
};
</script>

<style>
.input {
  font-size: 22px;
}
</style>
