<template>
  <div id="app">
  <nav class="navbar navbar-dark bg-dark" style="position: fixed; width:100%;">
      <div>
      <router-link to="/cine">
          <img src="./assets/popcorn.png">
      </router-link>
      <router-link to="/kid">
          <img src="./assets/kid.png">
      </router-link>
      <router-link to="/popular">
            <img src="./assets/top.png">
      </router-link>
      <router-link to="/genero">
            <img src="./assets/genero.png">
      </router-link>
      </div>
  </nav>
  <router-view></router-view>
  </div>
</template>

<script>

import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'

Vue.use(VueAxios, axios);

import BootstrapVue from 'bootstrap-vue';
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

Vue.use(BootstrapVue);

export default {
  name: 'app',
  data () {
    return {

    }
  },
}
</script>

<style>



</style>
