<template>
  <div class="home">
    <h1>This is my Home</h1>
    <v-container>
      <v-row>
        <v-col cols="10">
          <v-text-field
            name="name"
            label="Title"
            id="id"
            v-model="titleInput"
          ></v-text-field>
        </v-col>
        <v-col cols="2">
          <v-btn block color="success" @click="addTitle">Add</v-btn>
        </v-col>
      </v-row>

      <v-card>
        <v-card-title primary-title>
          <v-container>
            <v-row
              class="d-flex flex-row align-center"
              v-for="(item, index) in todos"
              :key="index"
            >
              <v-col cols="12" class="d-flex flex-row align-center">
                <v-checkbox v-model="value" value="value"></v-checkbox>
                <span>{{ item.title }}</span>
                <v-spacer></v-spacer>
                <v-btn color="error">x</v-btn>
              </v-col>
              <v-col cols="12"><v-divider></v-divider></v-col>
            </v-row>
          </v-container>
        </v-card-title>
      </v-card>
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Home",
  components: {},
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
    addTitle() {
      this.todos.push({
        id: Math.random,
        title: this.titleInput,
        completed: false,
      });
      this.titleInput = "";
    },
  },
};
</script>
