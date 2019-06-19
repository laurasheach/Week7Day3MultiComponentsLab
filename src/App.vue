<template>
  <div id="app">
    <h1>Countries of the World</h1>
      <div class="main-container">
        <!-- <countries-list :countries='countries'></countries-list> -->
        <country-select :countries='countries'></country-select>
        <country-detail :country='selectedCountry'></country-detail>
      </div>
  </div>
</template>

<script>
import {eventBus} from './main.js';
// import CountriesList from './components/CountriesList.vue';
import CountryDetail from './components/CountryDetail.vue';
import CountrySelect from './components/CountrySelect.vue';
export default {
  name: 'app',
  data(){
    return {
      countries: [],
      selectedCountry: null
    };
  },
  components: {
    // "countries-list": CountriesList,
    "country-select": CountrySelect,
    "country-detail": CountryDetail
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(result => result.json())
    .then(countries => this.countries = countries);
    eventBus.$on('country-selected', (country) => {
      this.selectedCountry = country;
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
}

ul {
    list-style-type: none;
}

</style>
