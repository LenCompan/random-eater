<template>
  <div id="app" class="container">
    <HelloWorld msg="Random Eater"/>
	<input v-model="message" placeholder="Import json url">
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
			random: null,
			message: null,
			old_message: null
		}
	},
	methods: {
		getAPlace: function () {
			if (this.message != null && this.old_message != this.message) {
				this.old_message = this.message;
				this.getJson();
				return ;
			}

			this.random = Math.floor(Math.random() * Math.floor(this.jsonData.length));
		},
		getJson: function () {
			axios.get(this.message).then( (res) => {
				this.jsonData = res.data;
				this.random = Math.floor(Math.random() * Math.floor(this.jsonData.length));
			});
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
