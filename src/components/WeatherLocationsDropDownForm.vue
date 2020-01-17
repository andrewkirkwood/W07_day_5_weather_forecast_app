<template lang="html">
  <select v-on:select.prevent>
    <option v-on:change="handleSelect" v-for="city in cities"> {{ city.title}}</option>
  </select>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'weather-drop-down-form',
  props: ['cities'],
  methods: {
    handleSelect: 
  }
}
</script>

<style lang="css" scoped>
</style>
