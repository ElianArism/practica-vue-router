<template>
  <div class="home">
    <Titulo text="Titulo del home" />
    <img alt="Vue logo" src="../assets/logo.png">
  </div>
</template>

<script>

// Componentes 
import Titulo from '../components/Titulo'

export default {
  name: 'Home',
  // Componentes externos
  components: {
    Titulo
  }
}
</script>
