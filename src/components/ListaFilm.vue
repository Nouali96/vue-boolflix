<template>
    <div class="container_films">
        <FilmCard v-for="(film, index) in films" :key="index" :film="film"/>             
    </div>   
</template>

<script>
    import FilmCard from './FilmCard.vue';
    export default {
        name: 'ListaFilm',
        props: {
            'films': Array
        },
        components: {
            FilmCard
        }
    }

</script>

<style lang="scss">
@import "../assets/style/general.scss";
.container_films{
    display: flex;
    flex-direction: row ;
    flex-wrap: wrap;
    justify-content: center;
}
</style>