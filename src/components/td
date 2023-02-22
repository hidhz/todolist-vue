<script>
  import './../todo.css'
  export default{
    props: {
      method: Function
    },
    data(){
      return {
        taskData: "",
        isDone: false,
        data: JSON.parse(localStorage.getItem("todos")) ? JSON.parse(localStorage.getItem("todos")) : "",
        jumlahselesai: 0
      }
    },
    methods: {
      getNew(){
        this.data = JSON.parse(localStorage.getItem("todos")) ? JSON.parse(localStorage.getItem("todos")) : ""
        const b = this.data.filter(d => {
          return d.isDone === true
        })
        this.jumlahselesai = b.length < 10 ? `0${b.length}` : b.length
      },
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
          let newTodo = JSON.parse(getTodo)
          newTodo.push(todo)
          localStorage.setItem("todos", JSON.stringify(newTodo))
          this.taskData = ""
          this.getNew()
        }
      },
      removeTodo(id){
        const newTodo = this.data.filter((data) => {
          return data.id !== id
        })
        localStorage.setItem("todos", JSON.stringify(newTodo))
        this.getNew()
      },
      doneTodo(data){
        const newTodo = this.data.map((item) => {
          if(item.id == data.id) {
            item.isDone = data.checked
          }
          return item
        })
        localStorage.setItem("todos", JSON.stringify(newTodo))
        this.getNew()
      },
      taskEdit(data){
        const newTodo = this.data.map((item) => {
          if(item.id == data.id) {
            item.task = data.value
          }
          return item
        })
        localStorage.setItem("todos", JSON.stringify(newTodo))
        this.getNew()
      },
    },
    mounted(){
      this.getNew()
    }
  }  
</script>

<template>
  <header>
    <h1>Todo App</h1>
    <div>
      <button>Semua <span>{{data.length < 10 ? 0 + ""+data.length : data.length}}</span></button>
      <button>Selesai <span>{{jumlahselesai}}</span></button>
    </div>
  </header>
  <div class="add-container">
    <input type="text" v-model="taskData" class="input-text" placeholder="tambah..." />
    <button @click="handleClick">tambah</button>
  </div>
  <span class="subtitle">all task</span>
  <div class="item-container">
    <div v-if="data.length > 0" v-for="item in data" class="item-item" key="item.id">
      <input @input="taskEdit($event.target)" :id="item.id" type="text" v-model="item.task" class="input-text"/>
      <input :id="item.id" :checked="item.isDone" @input="doneTodo($event.target)" type="checkbox" v-model="item.isDone" class="input-checkbox" />
      <button @click="removeTodo(item.id)">
        <img width="36" src="https://cdn-icons-png.flaticon.com/512/3817/3817209.png" alt="" />
      </button>
    </div>
    <div v-else><i>tidak ada data...</i></div>
  </div>
</template>