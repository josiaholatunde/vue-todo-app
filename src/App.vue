<template>
  <div id="app">
    <Header />
    <router-view></router-view>
<!--     <AddTodo @addTodo='addTodo' />
    <TodoList v-bind:todos='todos' @delTodo='deleteTodo' /> -->
  </div>
</template>

<script>
  import TodoList from './components/TodoList';
  import AddTodo from './components/AddTodo';
  import Header from './components/layouts/Header';
  import uuid from 'uuid';
  import axios from 'axios';
export default {
  name: 'app',
  components: {
    TodoList,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: []
    }
    
  },
  async created() {
    const response = await axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10');
    this.todos = [...response.data];
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(title) {
      const newTodo = {
        id: uuid.v4(),
        title,
        isCompleted: false
      }
      this.todos.push(newTodo);
    }
  }
}
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }
</style>
