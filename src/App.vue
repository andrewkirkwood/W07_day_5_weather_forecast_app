<template>
  <div id="app">
    <h1>Rain Check</h1>
    <weather-locations-drop-down-form :cities="allCities"/>
    <weather-locations-list :cities="allCities"/>
  </div>
</template>

<script>
import WeatherLocationsDropDownForm from './components/WeatherLocationsDropDownForm.vue'
import WeatherLocationsList from './components/WeatherLocationsList.vue'
import { eventBus } from './main.js'

export default {
  data(){
    return {
      allCities: [],
      savedCities: [],
      selectedCity: {}
    }
  },
  name: 'app',
  components: {
    "weather-locations-list": WeatherLocationsList,
    "weather-locations-drop-down-form": WeatherLocationsDropDownForm

  },
  mounted() {
    fetch("http://localhost:3000/edinburgh")
    .then(res => res.json())
    .then(edinburgh => this.allCities.push(edinburgh))
    fetch("http://localhost:4000/aberdeen")
    .then(res => res.json())
    .then(aberdeen => this.allCities.push(aberdeen))
  }
}
</script>

<style>
/* #app {
font-family: 'Avenir', Helvetica, Arial, sans-serif;
-webkit-font-smoothing: antialiased;
-moz-osx-font-smoothing: grayscale;
text-align: center;
color: #2c3e50;
margin-top: 60px;
} */
</style>
