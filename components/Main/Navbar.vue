<template>
    <div class="bg-gray-100 px-3 py-4 shadow-md">
       <NuxtLink class="bg-green-300 px-3 py-1 pb-1 hover:bg-green-400 rounded-full" to="/">Home</NuxtLink>
       <NuxtLink class="bg-green-300 px-3 py-1 pb-1 hover:bg-green-400 rounded-full ml-3" to="/NewTodo">New Todo</NuxtLink>
    </div>
</template>
 
<script>
export default{
    name:"navbar",
}
</script>