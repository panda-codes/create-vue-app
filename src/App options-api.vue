<script>
  export default{
    data(){
      return{
        message:"is the best",
        status:"pending",
        tasks:["Task One","Task Two","Task Three"],
        link:"https://erf.ng"
      }
    },
    methods:{
      toggleStatus(){
      this.status==='active'?this.status='pending':
      this.status==='pending'?this.status='inactive':
      this.status='active'
    }
    }
  }
</script>


<template>
  <div class="box">
  <h1>Vue Jobs {{message}}</h1>
  <h3 v-if="status==='active'">User is Active</h3>    
  <h3 v-else-if="status === 'pending'">User is Pending</h3>    
  <h3 v-else>User is Inactive</h3>
  
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
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