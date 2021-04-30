<template>
  <Titulo text="texto articulo" />
  
    <!-- Obtener parametros url -->
  <h2>Parametro: {{$route.params.id}}</h2>

  <div class="card">
      <p>{{ articulo.title}}</p>
      <p>{{ articulo.body}}</p>
  </div>
</template>

<script>

// Componentes  
import Titulo from '../components/Titulo.vue'

export default {
  // Componentes externos 
  components: { Titulo },

  // Datos del componente 
  data() {
    return {
      articulo: {},   
    }
  }, 

  // Created 
  created() {
      this.traerArticuloEspecifo()
  },

  // Funciones del componente
  methods: {
    async traerArticuloEspecifo() {
        //  Obtener parametros url
        const {id} = this.$route.params
        const data = await fetch(`https://jsonplaceholder.typicode.com/posts/${id}`)
        const articulo = await data.json()
        this.articulo = {...articulo}
    }
  }
}
</script>

<style scoped>
    .card {
        margin: auto;
        width: 300px;
        height: 300px;
        border-radius: 10px;
        border: 1px solid black;
        color: white;
        background-color: #444;
    }
</style>