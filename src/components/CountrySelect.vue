<template lang="html">
<div>
  <label for="select-a-country">Select a country: </label>
  <select v-on:change="handleSelected">
    <option v-for="(country, index) in countries" :country="country" :key="index">{{country.name}}</option>
  </select>
</div>
</template>

<script>

import {eventBus} from '../main.js'

export default {
  name: 'countries-list',
  props: ['countries', 'country'],
  methods: {
    handleSelected(){
      // eventBus.$emit('country-selected', this.country)
      console.log('country', this.country);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
