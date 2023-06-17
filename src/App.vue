<template>
  <center>
<<<<<<< HEAD
    <div id="main">
      <h1>Geuss The Country</h1>
      <img v-if="flagURL" :src="flagURL" :alt="countryName" style="height: 50%; width: 50%;">
      <form @submit.prevent="submitForm">
        <input type="text" placeholder="Enter Country Name.." v-model="countryName"><br>
        <button type="submit" >Enter</button>
      </form>
    </div>
  </center>
</template>

<script>
  import axios from 'axios'
  import { ref } from 'vue'
=======
  <div id="main">
    <h1>Geuss The Country</h1>
    <img v-if="Country.length > 0" :src="getCountryFlag('Eritrea')" alt="Country Flag" style="height: 50%; width: 50%;">
    <form @submit="PostData" method="post">
      <input type="text" name="Guess" placeholder="Enter Country Name.." id="Guess"><br>
      <button type="submit" name="submit">Enter</button>
    </form>
  </div>
  </center>
</template>
  
<script>
import axios from 'axios'
import { ref } from 'vue'
let Guess = document.getElementById("Guess")
>>>>>>> 73c3bc1982cdc172ae3dbb00c0ef1866c4d12264
  export default{
    data(){
      
    },

    setup(){
      const countryName = ref('')
      const flagURL = ref('')

<<<<<<< HEAD
      const submitForm = () => {
        axios.get(`https://restcountries.com/v2/name/${countryName.value}`).then(response => {
          const country = response.data[0];
          if(country){
            flagURL.value = country.flags.png || '';
          } else {
            flagURL.value = '';
          }
        })
        .catch( error =>{
          console.log(error)
          flagURL.value = '';
        })
      }
      return{
        submitForm, flagURL, countryName
=======
      axios.get("https://restcountries.com/v3.1/all")
      .then(Response => {
        Country.value = Response.data
      })
      .catch( error =>{
        console.log(error)
      })

      function getCountryFlag() {
        const country = Country.value.find(c => c?.name?.common === countryName);
        return country?.flags?.svg || '';
        
      }

      return{
        Country,        
        getCountryFlag
>>>>>>> 73c3bc1982cdc172ae3dbb00c0ef1866c4d12264
      }
    }
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