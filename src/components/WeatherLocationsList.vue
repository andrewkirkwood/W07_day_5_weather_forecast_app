<template lang="html">
  <div class="">
    <ul>
      <li v-for="city in cities">
        <h2>{{ city.title }}</h2>
        <table>
          <tr>
            <th>Time</th>
            <th>Weather State</th>
            <th>Min-temp</th>
            <th>Max-temp</th>
          </tr>
          <tr v-for="item in city.consolidated_weather">
            <td >{{ item.created }}</td>
            <td >{{ item.weather_state_name }}</td>
            <td>{{ Math.round(item.min_temp)}}</td>
            <td>{{ Math.round(item.max_temp) }}</td>
          </tr>
        </table>
        <button v-model="cityToBeDeleted" type="button"  :value="city" v-on:click="handleUnfavourite(city.woeid)">delete from favourites</button>

      </li>
    </ul>
  </div>

</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'weather-locations-list',
  data() {
    return {
      cityToBeDeleted: {}
    }
  },
  props: ['cities'],
  methods: {
    handleUnfavourite (id) {
      eventBus.$emit('delete-city-from-favourites', id)
    }

  }
}
</script>

<style lang="css" scoped>
</style>
