<template>
  <div class="todo-add">
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
  </div>
</template>

<script>
export default {
  name: "TodoAdd",
  methods: {
    addTitle() {
      this.$emit("onSubmitTodo", this.titleInput);
      this.titleInput = "";
    },
  },
  data() {
    return {
      titleInput:""
    }
  },
};
</script>

<style></style>
