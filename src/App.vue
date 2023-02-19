<script setup>
 // import TodoHeader from "./components/TodoHeader.vue"
//  import TodoItem from "./components/TodoItem.vue"
//  import TodoTambah from "./components/TodoTambah.vue"
  import Todo from "./components/Todo.vue"
</script>

<template>
  <div class="container">
    
    <Todo />
  </div>
</template>

<style>
  .container{
    margin: 15px;
  }
  .todo-item span{
    font-family: Arial;
    color: #64748b;
  }
</style>