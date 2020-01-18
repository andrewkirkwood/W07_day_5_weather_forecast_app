<template lang="html">
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
          <td>{{ item.min_temp }}</td>
          <td>{{ item.max_temp }}</td>
        </tr>
      </table>

    </li>
  </ul>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'weather-locations-list',
  props: ['cities'],
  methods: {

  }
}
</script>

<style lang="css" scoped>
</style>
