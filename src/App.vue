<template>
  <div class="app">
    <Navbar></Navbar>
    <CountriesList v-if="data" :data="data"></CountriesList>
    
  </div>
</template>

<script>

import Navbar from './components/Navbar.vue'
import CountriesList from './components/CountriesList.vue'



export default {
  components: {
    Navbar,
    CountriesList,
    
  },

  data() {
    return {
      data: []
    }
  },


  async created() {
    const response = await fetch(`https://ih-countries-api.herokuapp.com/countries/`)
    this.data = await response.json()

  }



}

</script>

<style>

</style>