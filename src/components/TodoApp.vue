<template>
  <div class="container">
  <h2 class="text-center mt-5">Todo App</h2>
  <!-- input -->
  <div class="d-flex">
    <input v-model="task" type="text" placeholder="Enter text" class="form-control ">
    <input v-model="status" type="text" placeholder="Enter Status" class="form-control">
    <button @click="submitTask" class="btn btn-warning rounded-0">SUBMIT</button>
  </div>
    <!-- Task Table -->
    <table class="table table-bordered mt-5">
  <thead>
    <tr>
      <th scope="col">Task</th>
      <th scope="col">Status</th>
      <th scope="col" class="text-center">#</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(task,index) in tasks" :key="index">
      <td>{{task.name}}</td>
      <td>{{task.status}}</td>
      <td>
        <div class="text-center" @click="deleteTask(index)">
          <span class="fa fa-trash"></span>
        </div>
      </td>
    </tr>
  </tbody>
</table>
  </div>
</template>

<script>
export default {
  name: 'TodoApp',
  props: {
    msg: String
  },
  data(){
    return{
      task:'',
      status:'',
       tasks:[
      {
        name:'Read Book',
        status:'to-do'
      },
      {
        name:'Draw a Painting',
        status:'in-progress'
      }
    ]
    }
  },
  methods:{
    submitTask(){
      if(this.task.length===0&&this.status.length===0) return alert("Please enter a Task and Status");
      this.tasks.push({
        name:this.task,
        status:this.status.length==0?"to-do":this.status,
      })
      this.task="";
      this.status="";
    },
    deleteTask(index){
      this.tasks.splice(index,1);
    }
  }
  
};
</script>
<style scoped>
</style>
