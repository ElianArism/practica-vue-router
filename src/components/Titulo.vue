<template>
  <h1>{{text}}</h1>
</template>

<script>
export default {
    // Nombre del componente
    name: 'Titulo',
    // propiedades para comunicarse entre componentes 
    props: {
        text: String
    }
}
</script>

<style>

</style>