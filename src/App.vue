<template>
  <div class="container d-flex justify-content-center mt-4">
    <div id="app">
      <ToDo/>
    </div>
  </div>
  
</template>

<script>

import ToDo from './components/ToDo.vue'

export default {
  name: 'App',
  components: {
    ToDo
  }
}
</script>

<style>
@import 'https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css';
</style>
