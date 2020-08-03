<template>
  <div>
    <form v-on:submit="addTodo">
      <input type="text" name="title" v-model="title" placeholder="Add new todo item.">
      <input type="submit" name="submit" class="btn">
    </form>
  </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';

export default {
  name: "AddTodo",
  data() {
    return {
      title: ''
    }
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const newTodo = {
        id: uuidv4(),
        title: this.title,
        completed: false
      }

      this.$emit('add-todo', newTodo);
    }
  }
}
</script>

<style scoped>
  form {
    display: flex;
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
  }
  input[type="submit"] {
    flex: 2;
  }
</style>