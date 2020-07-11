<template>
  <div class="todo">
    <div class="title" v-on:click="markComplete">
      <label>
        <input type="checkbox" class="nes-checkbox" v-model="todo.checked" />
        <span>&nbsp;</span>
      </label>
      <del v-if="todo.checked">{{ todo.title }}</del>
      <span v-else>{{ todo.title }}</span>
    </div>
    <div class="space"></div>
    <button class="nes-btn is-error padding" @click="$emit('delete-todo', todo.id)">×</button>
  </div>
</template>


<script>
export default {
  name: "Todo",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.checked = !this.todo.checked;
    },
    removeTodo() {}
  }
};
</script>

<style>
.todo {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  font-size: 22px;
}

.todo label {
  margin: 0;
  padding-top: 10px;
}

.todo del {
  width: 100%;
}

.title {
  display: flex;
  align-items: center;
}

.nes-btn {
  width: 35px;
  font-size: 18px;
}
</style>
