<template lang="html">
  <div class="heading">
    <h1>Countries of the World</h1>
    <div class="main-container">
      <country-list :countries="countries"></country-list>
      <country-detail :country="selectedCountry"></country-detail>
    </div>
  </div>
</template>

<script>
import CountryList from './components/CountryList.vue';
import { eventBus } from './main.js';
import CountryDetail from './components/CountryDetail.vue';

export default {
  name: 'app',
  data(){
    return {
      countries: [],
      selectedCountry: null
    };
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(response => response.json())
    .then(countries => this.countries = countries);
    
    eventBus.$on('selected-country', (country) => {
      this.selectedCountry = country;
    });
  },
  components: {
    'country-list': CountryList,
    'country-detail': CountryDetail
  }
}
</script>

<style lang="css">
.heading {
  padding-left: 2em;
  padding-right: 2em;
}
.main-container {
  display: flex;
  justify-content: space-between;
  padding-right: 4em;
}
</style>
