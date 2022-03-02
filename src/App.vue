<template>
  <div id="app">
    <MyHeader title="BOOLFLIX" @search="getFilms"/>
    <MyMain :films="films"/>
    <ListaFilm/>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue';
import ListaFilm from './components/ListaFilm.vue';
import MyMain from './components/MyMain.vue';

const axios = require('axios');
export default {
  
  name: 'App',
  components: {
    MyHeader,
    MyMain,
    ListaFilm,
  },
  data() {
    return {
      films:[],
    }
  },
  methods: {
    getFilms(search) {
      console.log(search);
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=de1234c51ff755e48d04593330b5b33b&query='+search)
      .then((response )=> {
        console.log(response);
       this.films = response.data.results;
       axios.get('https://api.themoviedb.org/3/search/tv?api_key=e99307154c6dfb0b4750f6603256716d&language=it_IT&query='+search) 
       .then((response )=> {
        console.log(response);
        this.films = this.films.concat(response.data.results);  
      })
      .catch(function (error){
        //handle error
        console.log(error);
      });
      })
      .catch(function (error){
        //handle error
        console.log(error);
      }); 
      // .then(function (){
      //   // always executed
      // });
    }
  }
}

</script>

<style lang="scss">
@import "./assets/style/general.scss";
</style>
