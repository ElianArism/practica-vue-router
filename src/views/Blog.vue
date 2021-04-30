<template>
    <Titulo text="Titulo de mi blog" />
    <button @click="consumirAPI">Consumir API</button>

    <div class="grilla">
        <div class="card"  v-for="b in arrayBlog" :key="b.id">
            <p><strong><a><router-link :to="`/blog/${b.id}`"> {{b.title}} </router-link></a></strong></p>
            <p>{{b.body}}</p>
        </div>
    </div>
</template>

<script>

// Componentes 
import Titulo from "../components/Titulo"

export default {
    // Nombre del componente
    name: 'Blog',
    // Componentes externos
    components: {
        Titulo
    },
    data() {
        return {
            arrayBlog: [],
        }
    },
    // Ciclo de vida de vue: Created = Propiedad que sirve 
    // para ejecutar funciones ni bien se procesa el componente antes de pintar el template
    created() {
        this.consumirAPI();
    },
    // funciones del componente 
    methods: {
        async consumirAPI() {
            try {
                const data = await fetch(`https://jsonplaceholder.typicode.com/posts`) 
                const array = await data.json()
                this.arrayBlog = [...array]
            } catch (error) {console.log(error)}

        }
    }
}
</script>

<style scoped>
    .grilla {
        height: 100%;
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 10px;
        align-items: center;
        justify-items: center;
        margin: 0 auto;
        width: 80%;
        background-color: beige;
        padding: 1rem;
    }

    .card {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-items: center;
        text-align: justify;
        widows: 60%;
        border: 1px solid #ccc;
    }

</style>