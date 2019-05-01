<template lang="html">
  <div>
    <input class="search" type="text" name="search" v-model="searchText" placeholder="Search countries...">
    <p v-for="(country, index) in countries"></p>
  </div>
</template>

<script>
export default {
  name: 'search',
  props: ['countries'],
  data() {
    return {
      searchText: null
    }
  },
  computed: {
    filteredCountries(){
      if(this.searchText){
        return this.countries.filter((country) => {
          return country.name.startsWith(this.searchText);
        })
      }
      else {
        return this.countries;
      }
    }
  }
}
</script>

<style lang="css" scoped>
</style>
