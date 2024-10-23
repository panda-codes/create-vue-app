<script setup>
import { ref, reactive, onMounted} from 'vue';

  
    // Use ref for primitive values and reactive for objects
    const message = ref("is Great");
    const status = ref("pending");
    const tasks = ref(["Task One", "Task Two", "Task Three"]);
    const link = ref("https://erf.ng");
    const newTask=ref("")

      // methods
      const toggleStatus = () => {
      status.value==='active'?status.value='pending':
      status.value==='pending'?status.value='inactive':
      status.value='active'
  }

  const addNewTask=()=>{
    tasks.value.push(newTask.value);
    newTask.value=''
  }

  const deleteTask=(index)=>{
    tasks.value.splice(index,1);
    // console.log(tasks)
  }

  onMounted(async ()=>{
    try {
      const response= await fetch('https://jsonplaceholder.typicode.com/todos')
      const data = await response.json();
      tasks.value=data.map((task)=>task.title);
    } catch (error) {
      console.log("Error Fetching Task");
    }
  })
</script>


<template>
  <div class="box">
  <h1>Vue Jobs {{message}}</h1>
  <h3 v-if="status==='active'">User is Active</h3>    
  <h3 v-else-if="status === 'pending'">User is Pending</h3>    
  <h3 v-else>User is Inactive</h3>


<form @submit.prevent="addNewTask">
  <label for="newTask">New Task</label>
  <input type="text" id="newTask" v-model="newTask">
  <button type="submit">Submit</button>
</form>
  <ul>
    <li v-for="(task,index) in tasks" :key="task">
      <span>{{ task }}</span>
      <button @click="deleteTask(index)">x</button>
    </li>
  </ul>

  <!-- <a v-bind:href="link">click for erf</a> -->
  <a :href="link">click for erf</a>

  <!-- <button v-on:click="toggleStatus">change status</button> -->
  <button @click="toggleStatus">change status</button>
  </div>

</template>

<style scoped>
  .box{
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  h1{
    color: blue;
  }
  h3{
    color:purple;
  }
  
</style>