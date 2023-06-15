<template>
  <center>
  <div id="main">
    <h1>Geuss The Country</h1>
    <h1>{{ Country[100].flag }}</h1>
    <form method="post" action="App.vue">
      <input type="text" name="Geuss" placeholder="Enter Country Name.."><br>
      <button type="submit" name="submit">Enter</button>
    </form>
  </div>
  </center>
</template>
  
<script>
import axios from 'axios'
import { ref } from 'vue'

  export default{
    setup(){
      const Country = ref([])

      axios.get("https://restcountries.com/v3.1/all")
      .then(Response => {
        Country.value = Response.data
      })
      .catch( error =>{
        console.log(error)
      })
      return{
          Country
      };
    },
  }
</script>

<style>
  :root{
    --DarkGreen: #35495e;
    --LightGreen: #42b883;
    --White: rgb(232, 232, 232);
  }body{
    background-color: var(--DarkGreen);
  }

  #main{
    border: #42b883 solid 10px;
    width: 50%;
    margin: auto;
    margin-top: 10%;
    height: 65vh;
    border-radius: 20px;
    background-color: var(--White);
  }
</style>
