<template>
        <div class="container-card">
            <div class="card">
                <div class="front">
                    <img :src="'https://image.tmdb.org/t/p/w342' + film.poster_path"  :alt="film.title">
                </div>
                <div class="back">
                    <ul>
                        <li>Titolo: {{film.title}}</li>
                        <li>Titolo originale: {{film.original_title}}</li>
                        <li>Voto: <span v-for="star in getStars(film.vote_average)" :key="star" class="fa-solid fa-star"></span></li>
                        <li>Overview: {{film.overview}}</li>
                    </ul>
                </div>
            </div> 
        </div>           
</template>

<script>
export default {
    name: 'FilmCard',
    props :{
        'film': Object
    },
    methods:{
        getStars(stars){
            return parseInt((stars)/2)
        }
    }
}
</script>

<style lang="scss">
@import "../assets/style/general.scss";
    //star
    .fa-star{
        color: orange;     
    }
    //card
    .container-card {
        display: inline-block;
        perspective: 900px;
        width: 342px;
        height: 514px;
    }

    .card {  
        transition: all 0.6s ease;
        transform-style: preserve-3d;
        width: 100%;
        position: relative;
    }
    
    //hover-effect
    .front, .back {
        display: flex;
        position: absolute;
        backface-visibility: hidden; 
    }

    .front {
        font-size: 30px;
    }

    .back {
        font-size: 18px;
        background: black;
        top: 0;
        left: 0;
        height: 513px;
        width: 100%;
        color: white;
        padding-top: 10px;
        transform: rotateY(180deg);
    }
    .container-card:hover .card {
        transform: rotateY(180deg);
    }
</style>