<template>
  <div class="container">
    <div v-for='todo in todos' v-bind:key='todo.id' >
       <TodoItem 
      v-bind:todo='todo'
      @del-todo='handleDelete' 
    />
    </div>
  </div>
</template>
<script>
import TodoItem from './TodoItem';
export default {
  name: 'TodoList',
  props: ['todos'],
  components: {
    TodoItem
  },
  methods: {
    handleDelete(id) {
      this.$emit('delTodo', id);
    }
  }
}
</script>
<style lang="scss" scoped>

</style>
