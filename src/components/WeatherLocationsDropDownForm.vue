<template lang="html">
    <select v-on:change="handleSelect" >
      <option v-for="city in cities"> {{ city.title}}</option>
    </select>

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
    handleSelect() {
      eventBus.$emit('city-selected', this.selectedCity)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
