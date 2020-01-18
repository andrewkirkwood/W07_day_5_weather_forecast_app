<template lang="html">

  <div class="">


    <select v-on:change="handleSelect">
      <option v-for="city in cities" > {{ city.title}}</option>
    </select>
    <button type="button" v:on:submit="handeAddToFavourites" >Add to favourites</button>
</div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'weather-drop-down-form',
  data() {
    return {
      selectedCity: this.parentSelectedCity
    }
  },
  props: ['cities', 'parentSelectedCity'],
  methods: {
    handleAddtoFavourites() {
      eventBus.$emit('city-to-favourites', this.selectedCity)
    },
    handleSelect() {
      this.selectedCity = city
    }
  }
}
</script>

<style lang="css" scoped>
</style>
