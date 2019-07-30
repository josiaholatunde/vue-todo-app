<template>
  <div class="todo-item" v-bind:class='{ "is-complete": todo.isCompleted }'>
    <p> 
      <input type="checkbox" name="iscomplete" v-on:change='markComplete'>
      {{ todo.title }}
      <button class="del" @click='deleteTodo'>x</button>
    </p>
  </div>
</template>
<script>
export default {
  name: 'TodoItem',
  props: ['todo'],
  methods: {
    markComplete () {
      this.todo.isCompleted = !this.todo.isCompleted;
    },
    deleteTodo() {
      this.$emit('del-todo', this.todo.id);
    }
  }

}
</script>
<style lang="scss" scoped>
  .todo-item {
    background: #f4f4f4;
    border-bottom: 1px dotted #ccc;
    padding: 1rem;
  }
  .is-complete {
    text-decoration: line-through;
  }
  .del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    outline: none;
    float: right;
    cursor: pointer;
  }
</style>
