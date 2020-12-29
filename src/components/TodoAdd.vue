<template>
  <div class="todo-add">
    <v-row>
      <v-col cols="10">
        <v-text-field
          name="name"
          label="Title"
          id="id"
          @keyup.enter="addTitle"
          v-model="titleInput"
        ></v-text-field>
      </v-col>
      <v-col cols="2">
        <v-btn block color="success" @click="addTitle">Add</v-btn>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import { v4 as uuidv4 } from "uuid";

export default {
  name: "TodoAdd",
  methods: {
    addTitle() {
      // console.log(uuidv4());
      let task = {
        id:uuidv4(),
        title:this.titleInput,
        completed:false
      }
      // alert(task)
      this.$emit("onSubmitTodo", task);
      this.titleInput = "";
    },
  },
  data() {
    return {
      titleInput: "",
    };
  },
};
</script>

<style></style>
