<template lang="html">
  <div>
    <input class="search" type="text" name="search" v-model="searchText" placeholder="Search countries...">
    <p v-for="(country, index) in returnedCountries">{{country.name}}</p>
  </div>
</template>

<script>
export default {
  name: 'search',
  props: ['countries'],
  data() {
    return {
      searchText: null,
      returnedCountries: []
    }
  },
  computed: {
    filteredCountries(){
      if(this.searchText){
        console.log(this.searchText);
        return this.countries.filter((country) => {
          this.returnedCountries.push(country.name.startsWith(this.searchText));
        })
      }
      else {
        return 'Country Not Found';
      }
    }
  }
}
</script>

<style lang="css" scoped>
</style>
