<script>
  export default {
    props: {
      method: Function,
    },
    data(){
      return {
        taskData: ""
      }
    },
    methods: {
      handleClick(){
        const getTodo = localStorage.getItem("todos")
        const todo = {
          id: new Date().getTime(),
          task: this.taskData,
          isDone: false
        }
        if(!todo.task) return false
        if(!getTodo){
          localStorage.setItem("todos", JSON.stringify([todo]))
        } else{
          const newTodo = JSON.parse(getTodo)
          newTodo.unshift(todo) 
          localStorage.setItem("todos", JSON.stringify(newTodo))
          this.taskData = ""; this.method()
        }
      }
    },
  }
</script>

<template>
  <div class="add-container">
    <input type="text" v-model="taskData" class="input-text" placeholder="tambah..." />
    <button @click="handleClick">tambah</button>
  </div>
</template>