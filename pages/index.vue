<template>
  <div class="HomeIndex p-3">
    <div class="tasks-list w-1/2 p-4">
      <h3 class="text-2xl mb-4">Task List</h3>
        <div class="p-3 shadow-md border-2 rounded-md border-gray-300 mb-3" v-for="task in taskList">
          <div class="flex">
              <h5>{{ task.title }}</h5>
              <div>
                <button @click="destroy(task.id)">✘</button>
              </div>
          </div> 
        </div>
    </div>
  </div>
</template>
<script>
export default {
  layout:'Main', 
  data(){
    return{
      tasksFetchError:String,
      tasks:Array,
      taskList:[]
    }
  },
  methods: {
    async getTasks(){
      this.$axios.get('http://127.0.0.1:8000/api/tasks').then(response=>{
        if(response.status != 404){
          this.taskList = response.data;
        }else{
          this.tasksFetchError = "true";
        }
      }).catch(function(error){
        console.log(error.toJSON());
      });
      
    },
    destroy(id){
      this.$axios.delete('http://127.0.0.1:8000/api/tasks/'+id).then(response=>{
        //console.log(this)
        this.taskList = response.data;
      });
    }
  },
  beforeMount(){
    this.taskList = this.tasks;
  },
  mounted() {
    this.getTasks();
  },
}
</script>
 