<template>
  <div id="app">
    <h1>Scottish Rain Check</h1>
    <h4 >Select your favourite cities</h4 >
      <weather-locations-drop-down-form :cities="allCities" />
      <h3>Your saved cities</h3>
      <weather-locations-list :cities="savedCities"/>
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
        savedCities: []
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

      fetch("http://localhost:4000/dundee")
      .then(res => res.json())
      .then(dundee => this.allCities.push(dundee))

      fetch("http://localhost:4000/glasgow")
      .then(res => res.json())
      .then(glasgow => this.allCities.push(glasgow))

      eventBus.$on('city-to-favourites', city=> {
        if (!this.savedCities.includes(city)) {
          this.savedCities.push(city)
        }
      })

      eventBus.$on('delete-city-from-favourites', cityToBeDeleted => {
        const index = this.savedCities.indexOf(cityToBeDeleted)
        this.savedCities.splice(cityToBeDeleted, 1)
      })
    }
  }
  </script>

  <style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
    font-size: 0.75em;
  }
  </style>
