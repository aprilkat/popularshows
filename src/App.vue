<template>
  <div>
    <Header/>
    <Card/>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Card from './components/Card.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Card
  },

data(){
  return{
    shows: []
  }
},
mounted(){
  axios.get("https://api.themoviedb.org/3/tv/popular?api_key=1314a8e99666cc05df8ce544cd09f9f3&language=en-US&page=1").then ((response) => {
    this.shows = response.data.results;
  })

}}
</script>

<style>
 * {
  margin: 0px;
  padding: 0px;
  text-align: center;
}
</style>
