<template lang="html">
  <div class="">
    <select v-model="selectedCity">
      <option v-for="city in cities" :value="city"> {{ city.title}} </option>
    </select>
    <button type="button" v-on:click="handleAddToFavourites" >Add to favourites</button>
  </div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'weather-drop-down-form',
  data() {
    return {
      selectedCity: {}
    }
  },
  props: ['cities'],
  methods: {
    handleAddToFavourites() {
      eventBus.$emit('city-to-favourites', this.selectedCity)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
