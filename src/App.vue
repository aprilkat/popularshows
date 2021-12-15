<template>
  <div class = "content">
    <Header />
    <div></div>
    <Card  v-show="key <= 3" v-for="(show, key) in shows" v-bind:shows=shows v-bind:key=key v-bind:title=shows[key].name v-bind:overview=shows[key].overview v-bind:imglink=imglink v-bind:img=shows[key].poster_path />
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
    shows: [],
    imglink: 'https://www.themoviedb.org/t/p/w600_and_h900_bestv2',
    key: 0,

  }},



mounted(){

  axios.get( "https://api.themoviedb.org/3/tv/popular?api_key=1314a8e99666cc05df8ce544cd09f9f3&language=en-US&page=1").then (res => {
    this.shows = res.data.results;
  })}

}

</script>

<style>
 * {
  margin: 0px;
  padding: 0px;
  text-align: center;
}

.content {
  width: 100%;
  display: inline-block;
}
</style>
