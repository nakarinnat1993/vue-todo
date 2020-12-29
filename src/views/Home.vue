<template>
  <div class="home">
    <h1>This is my Home</h1>
    <v-container>
      <!-- Todo add -->
      <todo-add @onSubmitTodo="addTitle"/>

      <!-- Todo list -->
      <TodoList :todos="todos"/>

    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src
import TodoList from "@/components/TodoList.vue"
import TodoAdd from "@/components/TodoAdd.vue"

export default {
  name: "Home",
  components: {
    TodoList,
    TodoAdd
  },
  data() {
    return {
      titleInput: "",
      todos: [
        { id: 1, title: "Title 1", completed: false },
        { id: 2, title: "Title 2", completed: true },
        { id: 3, title: "Title 3", completed: false },
      ],
    };
  },
  methods: {
    addTitle(value) {
      this.todos.push({
        id: Math.random,
        title: value,
        completed: false,
      });
      this.titleInput = "";
    },
  },
};
</script>
