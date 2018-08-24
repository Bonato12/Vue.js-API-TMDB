<template>
  <div id="genero">

  <div  style="padding-top:100px; position:fixed; margin-left: 900px;">
      <select class="form-control form-control-lg"  v-model="selected" v-on:click="getGenero" >
                       <option v-for="g in genres" v-bind:value="g.value">{{g.name}} </option>
      </select>
  </div>

  <li v-for="item in movies" class="lista">
      <div class="card bg-dark text-white" style="width: 500px; height: 580px;">
          <img class="card-img" v-bind:src="imageUrl + item.poster_path" alt="Card image">
          <div class="card-img-overlay">
              <h5 class="card-title">{{item.original_title}}</h5>
              <p class="card-text stroke" >{{item.overview}}</p>
              <p class="card-text">{{item.release_date}}</p>
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
		 created: function() {


		},
		data () {
			return {
				imageUrl: 'https://image.tmdb.org/t/p/w342',
				selected: '28',
				 movies: [],
				 genres: [
			{ name: "Accion", value: '28' },
			{ name: "Animada", value: '16' },
			{ name: "Aventura", value: '12' },
			{ name: "Comedia", value: '35' },
			{ name: "Drama", value: '18' },
			{ name: "Fantasia", value: '14' },
			{ name: "Guerra", value: '10752' },
			{ name: "Romance", value: '10749' },
			{ name: "Terror", value: '27' },
			{ name: "Familia", value: '107' }
			]
			}
		},

		methods: {
				getGenero(){
				var genero = this.selected;
				var self = this;
				axios.get('https://api.themoviedb.org/3/discover/movie?api_key=1b62ccff88d2cd537027e1d82920197b&with_genres='+genero+'&sort_by=vote_average.desc&vote_count.gte=10')
				.then(function(response){
				self.movies = response.data.results;
				});
				}


		}
	}
</script>

<style>

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

#genero{

background-image: url("fondoGenero.jpg");
background-attachment: fixed;


}


</style>
