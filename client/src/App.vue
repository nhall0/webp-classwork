<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import NavBar from './components/NavBar.vue';

</script>

<template>
  <header>

    <NavBar/>
    
  </header>

  <body>
    <div class="container">
      <RouterView />
    </div>
  </body>
</template>

<style scoped>
  body {
    font-family: Helvetica, sans-serif;
  }

  .wrapper {
    text-align: center;
  }

  .container {
    max-width: 600px;
    margin: 0 auto;
    padding: 0 20px;
  }
</style>
```