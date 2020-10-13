<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="title" />
    <button class="addb" type="submit">Add</button>
  </form>
</template>


<script>
export default {
  data() {
    return {
      title: "",
    };
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false,
        };
        this.$emit("add-todo", newTodo);
        this.title = "";
      }
    },
  },
};
</script>


<style  scoped>
form {
  display: flex;
  justify-content: center;
}
input {
  width: 400px;
  border: none;
  border-bottom: 2px solid darkgray;
  outline: transparent;
}
.addb {
  margin-left: 0.5rem;
  border: none;
  outline: transparent;
}
</style>