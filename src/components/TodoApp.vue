<template>
  <div class="container" >
    <div class="row">
      <div class="col-md-4 text-center ">
        <h2 class="text-center mt-5">Add stories </h2>

   <!-- input  -->
   <div class="d-flex">
     
     <button @click="submitTask" class="btn btn-warning rounded-0 text-center"> Add</button>
   </div>

   <!-- table -->
   <table class="table table-bordered">
  <thead>
    <tr >
      <th scope="col" class="text-center">Task</th>
      <!-- <th scope="col" class="text-center">status</th> -->
      <!-- <th scope="col" class="text-center">#</th> -->
      <!-- <th scope="col" class="text-center">#</th> -->
    </tr>
  </thead>
  <tbody>
    <tr v-for="(task, index) in tasks" v-bind:key ="index" v-bind="index" >
      <td class=" text-success"  scope="row">{{task.name}}</td>
      <!-- <td>{{task.status}} </td> -->
      <td>
        <div class="text-center" @click="editTask(index)">
          <span class="fa fa-pen"></span>
        </div>
      </td>
      <td>
        <div class="text-center" @click="deleteTask(index)">
          <span  class="fa fa-trash"></span>
        </div>
      </td>
    </tr>
    <tr>
      <input v-model="task" type="text" placeholder="add stories" class="form-control">
    </tr>
    
  </tbody>
</table>
      </div>
    </div>
   
   
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return{
      task: 'hello ',
      editedTask : null,
      tasks:[
        {
          name: 'hope you get it ',
          status: 'to-do'
        },
        {
          name: 'all is well ',
          status: 'to-do- now '
        }
      ]
    }
  },
  methods: {
    submitTask(){
      // console.log("clicked");
      if(this.task.length === 0) return;


      if(this.editedTask === null){
      this.tasks.push({
        name: this.task,
        status: 'to-do'
      });
      } else{
        this.tasks[this.editedTask].name = this.task;
        this.editedTask = null;
      }


      this.task = ''
    },

    deleteTask(index){
      this.tasks.splice(index,1);
    },

    editTask(index){
      this.task = this.tasks[index].name;
      this.editedTask = index;

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
