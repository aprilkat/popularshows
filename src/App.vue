<template>

    <!--
        Author: April Bollinger
        Date: 12/11/2021
        Program: Vue Popular Shows (App Component)
     -->

  <div class = "content">
    <Header />
    <!--I used a v-show with a v-for even though you are not supposed to. The v-show would not work right elsewhere. -->
    <!--I also bind everything to the Card component right here -->
    <Card  v-show="key <= 3" v-for="(show, key) in shows" v-bind:shows=shows v-bind:key=key v-bind:title=shows[key].name v-bind:overview=shows[key].overview v-bind:imglink=imglink v-bind:img=shows[key].poster_path />
  </div>
</template>



<script>
// Importing everything needed.
import Header from './components/Header.vue';
import Card from './components/Card.vue';
import axios from 'axios';

// Exporting everyhting needed.
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


// API Call using Axios

mounted(){

  axios.get( "https://api.themoviedb.org/3/tv/popular?api_key=1314a8e99666cc05df8ce544cd09f9f3&language=en-US&page=1").then (res => {
    this.shows = res.data.results;
  })}

}

</script>



<style>
/* base styles for all components */
 * {
  margin: 0px;
  padding: 0px;
  text-align: center;
}

/* container */

.content {
  width: 100%;
  display: inline-block;
}
</style>
