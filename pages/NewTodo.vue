<template>
    <div class="NewTodo p-3 h-screen flex mt-[40px] justify-center"> 
        <form @submit.prevent="addTodo" action="" method="POST">
            <div class="form-group w-[400px] flex flex-col p-4 shadow-md rounded">
                <h4 class="text-xl mb-3">Add New todo</h4>
                <label for="" class="mb-2">Title</label>
                <input v-model="todo.title" type="text" name="title" id="title" class="form-control border-2 border-gray-400 px-3 py-1 mb-2 rounded-full" placeholder="Title.." aria-describedby="helpId">
              <div>
                <button class="py-1 px-3 text-white rounded-full bg-rose-400 mt-2" type="submit">Add</button>
              </div>
            </div>
        </form>
    </div>
</template>
<script>
export default{
    layout:'Main',
    data(){
        return {
            todo:{
                title:'sas'
            }
        }
    },
    methods:{
        async addTodo(){
            this.$axios.post('http://127.0.0.1:8000/api/tasks',this.todo).then(function(response){
                console.log(response);
            }).catch(function(error){
                console.log(error);
            }).finally(function(){
                console.log("done");
            });
        },
        async getTasks(){
            this.$axios.get('http://127.0.0.1:8000/api/tasks').then(response=>{
                console.log(response);
            });
        }
    },
    mounted(){
        this.getTasks();
    }
}
</script>