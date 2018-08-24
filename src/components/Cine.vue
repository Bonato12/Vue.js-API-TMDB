<template>
  <div id="cine">


  <li v-for="item in movies" class="lista">



  <div class="card bg-dark text-white" style="width: 500px; height: 580px;">
  <img class="card-img" v-bind:src="imageUrl + item.poster_path" alt="Card image">
  <div class="card-img-overlay">
    <h5 class="card-title stroke">{{item.original_title}}</h5>
    <p class="card-text stroke" >{{item.overview}}</p>
    <p class="card-text stroke">{{item.release_date}}</p>
  </div>
</div>


  </li>

  </div>
</template>

<script>

import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'

Vue.use(VueAxios, axios);

export default {
  data () {
    return {
    imageUrl: 'http://image.tmdb.org/t/p/w342',
    movies: [],
    }
  },
  created(){

  this.getCine()

  },

  methods:{

  getCine(){
  var self = this;
  axios.get('https://api.themoviedb.org/3/discover/movie?api_key=b835ed932f4f0a4532e2512ff3cce439&primary_release_date.gte=2018-08-1&primary_release_date.lte=2018-08-17')
  .then(response => (self.movies = response.data.results))
  }

  }


}
</script>

<style>

#cine{

background-image: url("fondoCine.jpg");
background-attachment: fixed;





}

.stroke {
text-align:center;
color: #000;
font-family: impact;
font-size: 20px;
text-shadow: -2px -2px 0px #fff, 2px -2px 0px #fff, -2px 2px 0px #fff, 2px 2px 0px #fff;
}

.lista{

padding-top: 100px;
margin-left: 370px;
list-style:none;

}



</style>
