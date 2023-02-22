<script>
  export default {
    props: {
      semuaTask: Number,
      taskSelesai: Number,
    }
  }
</script>
<template>
  <header>
    <h1>Todo App</h1>
    <div>
      <button>Semua <span>{{semuaTask}}</span></button>
      <button>Selesai <span>{{taskSelesai}}</span></button>
    </div>
  </header>
</template>