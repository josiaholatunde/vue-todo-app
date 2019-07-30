<template>
  <div class="container mt-5">
    <form>
    <div class="form-group">
      <input type="text" name="todo" class="form-control" v-model="title">
      <input type="button" class="btn btn-danger btn-md mt-2" value="Add" @click='addTodo'>
    </div>
  </form>
  </div>
</template>


<script>
export default {
  name: 'AddTodo',
  data() {
    return {
      title: ''
    }
  },
  methods: {
    addTodo() {
      this.$emit('addTodo', this.title);
      
      this.title = '';
    }
  }
}
</script>

<style lang="">
  
</style>