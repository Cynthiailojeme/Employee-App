<template>
  <div id="app">
    <navbar/>
    
    <router-view/>
  </div>
</template>

<script>
import navbar from '@/components/navbar.vue'

export default {
  name: 'App',
  components: {
    navbar
  }
}
</script>


<style>
  body{
  background: #148489;
  font-family: 'Roboto', sans-serif;
  color: #ffffff;
}
</style>
