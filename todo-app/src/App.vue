<template>
  <div id="app" class="container">
    <div class="date_wrap">
      <div class="month">{{ moment().format("MMM") }}</div>
      <div class="date">{{ moment().format("D") }}</div>
      <div class="day">{{ moment().format("dddd") }}</div>
    </div>
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:delete-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from "./components/Todos";
import AddTodo from "./components/AddTodo";
import moment from "moment";
import "nes.css/css/nes.min.css";

export default {
  name: "App",
  components: { Todos, AddTodo },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Go workout",
          checked: true,
        },
        {
          id: 2,
          title: "Do laundry",
          checked: false,
        },
        {
          id: 3,
          title: "Cook food",
          checked: false,
        },
        {
          id: 4,
          title: "Clean up room",
          checked: true,
        },
        {
          id: 5,
          title: "Finish work",
          checked: false,
        },
      ],
      date: null,
    };
  },
  methods: {
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    },
    deleteTodo(todoId) {
      this.todos = this.todos.filter((todo) => todo.id !== todoId);
    },
    moment,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=VT323&display=swap");

html,
body,
pre,
code,
kbd,
samp,
h2 {
  font-family: "VT323", monospace;
}

ul {
  margin: 0;
  padding: 0;
}

label {
  display: block;
}

.container {
  width: 600px;
  margin: 50px auto;
  text-align: left;
}

body {
  padding: 20px;
}

#app {
  background: #fff;
  border-radius: 4px;
  padding: 20px;
  transition: all 0.2s;
}

li {
  margin: 8px 0;
}

del {
  color: rgba(0, 0, 0, 0.3);
}

.padding {
  padding: 1px 7px 2px;
}

.space {
  flex-grow: 1;
}

.date_wrap {
  position: relative;
  display: inline-flex;
  margin-bottom: 50px;
}

.month {
  font-size: 36px;
  margin-left: 10px;
  position: absolute;
  right: -50px;
  line-height: 40px;
}

.date {
  position: relative;
  font-size: 100px;
  line-height: 70px;
}

.day {
  font-size: 36px;
  margin-left: 10px;
  position: absolute;
  right: -93px;
  bottom: 0;
  line-height: 38px;
}
</style>
