<template>
  <div class="text-capitalize text-black-50">
    Todo App Live
    <div v-for="todo in todos" v-bind:key="todo.id">
      {{ todo.text }}
      <button @click="removeTodo(todo.id)">x</button>
    </div>
    <div>
      <input type="text" v-model="todo" placeholder="Add todo......"/>
      <button @click="addTodo" class="btn btn-primary bg-dark m-1 p-2">add</button>
      <button @click="clearAll" class="btn btn-danger bg-gradient m-1 p-2">Clear All</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      todos: [
        {
          id: Math.random(),
          text: 'World'
        },
        {
          id: Math.random(),
          text: 'Math'
        },
      ]
    }
  },
  methods: {
    removeTodo(todoId) {
      this.todos = this.todos.filter((todo) => todo.id !== todoId);
    },
    addTodo() {
      if (this.todo.length === 0) {
        return;
      }else {
        this.todos.push({
          id:Math.random(),
          text: this.todo,
        })
        this.todo='';
      }
    },
    clearAll(){
      this.todos=[];
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

@import "~bootstrap/dist/css/bootstrap.min.css";
</style>
