<template>
  <div class="home">
    <h1>This is my Home</h1>
    <v-container>
      <!-- Todo add -->
      <todo-add @onSubmitTodo="addTitle" />

      <!-- Todo list -->
      <TodoList @onRemove="removeTitle" :todos="todos | reversed" />
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src
import TodoList from "@/components/TodoList.vue";
import TodoAdd from "@/components/TodoAdd.vue";
import axios from "axios";

export default {
  name: "Home",
  components: {
    TodoList,
    TodoAdd,
  },
  data() {
    return {
      titleInput: "",
      todos: [],
      todos_mockup: [
        { id: 1, title: "Title 1", completed: false },
        { id: 2, title: "Title 2", completed: true },
        { id: 3, title: "Title 3", completed: false },
      ],
    };
  },
  async mounted() {
    let result = await axios.get("https://jsonplaceholder.typicode.com/todos");
    this.todos = result.data;
  },
  filters:{
    reversed(value){
      return value.slice().reverse()
    }
  },
  computed:{
    reverseTodo(){
      return this.todos.slice().reverse()
    }
  },
  methods: {
    async addTitle(task) {
      let result = await axios.post("https://jsonplaceholder.typicode.com/todos", task);
      // alert(JSON.stringify(result.data));
      this.todos.push(result.data);
    },
    removeTitle(id) {
      if (confirm("Are you sure ?")) {
        this.todos = this.todos.filter((item) => item.id !== id);
      }
    },
  },
};
</script>
