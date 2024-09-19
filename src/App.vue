<template>
  <div class="focus">
       <input type="text" ref="input">
       <br><br>
       <button v-on:click="getData">Focus</button>
   </div>

</template>

<script>
export default {
 name: 'App',
 methods:{
   getData()
   {
     this.$refs.input.focus();
   }
 }
}
</script>

<style>
.focus {
   display: flex;
   flex-direction: column;
   align-items: center;
   justify-content: center;
   padding: 30px;
   background-color: #f0f4f8;
   border-radius: 10px;
   box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
   max-width: 300px;
   margin: 50px auto;
}

input[type="text"] {
   width: 100%;
   padding: 10px;
   border: 1px solid #ccc;
   border-radius: 5px;
   font-size: 16px;
   outline: none;
   transition: border 0.3s ease;
}

input[type="text"]:focus {
   border-color: #3498db;
   box-shadow: 0 0 5px rgba(52, 152, 219, 0.5);
}

button {
   background-color: #3498db;
   color: white;
   padding: 10px 20px;
   border: none;
   border-radius: 5px;
   font-size: 16px;
   cursor: pointer;
   transition: background-color 0.3s ease;
   margin-top: 10px;
}

button:hover {
   background-color: #2980b9;
}

button:active {
   background-color: #2471a3;
}


</style>
