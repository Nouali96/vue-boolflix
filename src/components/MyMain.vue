<template>
    <main>
        <ListaFilm :films='films'/>
    </main>
</template>

<script>
    import ListaFilm from './ListaFilm.vue';
    export default {
        name: 'MyMain',
        props: {
            'films': Array,
        },
        components: {
            ListaFilm
        }
    }
</script>

<style lang="scss">

</style>