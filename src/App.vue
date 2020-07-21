<template>
  <div id="app" class="container">
    <HelloWorld msg="Random Eater"/>
	<button v-on:click="getAPlace()" class="btn btn-success">Let's Start !</button>
	<div class="row">
		<PlaceCard v-if="random !== null" v-bind:place="jsonData[random]" />
	</div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import PlaceCard from './components/PlaceCard.vue'
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'
import json from './json/data.json'
import axios from 'axios'

export default {
	name: 'App',
	components: {
		HelloWorld,
		PlaceCard
	},
	data() {
		return {
			jsonData: json,
			random: null
		}
	},
	methods: {
		getAPlace: function () {
			this.random = Math.floor(Math.random() * Math.floor(this.jsonData.length));
		}
	},
	mounted () {
		axios.get('https://devel.perrotin.com/random-eater/data.json')
		.then( res => { this.jsonData = res.data} );
	}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
