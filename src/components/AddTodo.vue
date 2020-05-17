<template>
  <div>
    <form @submit="addTodo">
      <input
        type="text"
        v-model="title"
        name="title"
        placeholder="할 일 추가"
      />
      <input type="submit" value="추가" class="btn" />
    </form>
  </div>
</template>

<script>
// import { v4 as uuidv4 } from 'uuid';
export default {
  name: "AddTodo",
  data() {
    return {
      title: "",
    };
  },
  methods: {
    addTodo(e) {
      // form event prevent
      e.preventDefault();

      const newTodo = {
        title: this.title,
        completed: false,
      };
      // Send up to parent
      this.$emit("add-todo", newTodo);
      // Reset text-input
      this.title = "";
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
}

input[type="text"] {
  flex: 10;
  padding: 4px;
}
input[type="submit"] {
  flex: 2;
}
</style>
