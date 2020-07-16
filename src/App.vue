<template>
  <div id="app" class="container">
    <HelloWorld msg="Random Eater"/>
	<button v-on:click="test()" class="btn btn-success">Let's Start !</button>
	<div class="row">
		<PlaceCard v-bind:place="jsonData[random]" />
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
			random: 0
		}
	},
	methods: {
		test: function () {
			this.random = Math.floor(Math.random() * Math.floor(this.jsonData.length))

			axios.get("https://www.reddit.com", { crossdomain: true }).then( res => { console.log(res) })
		}
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
