<template lang="html">
  <div v-if="country">
    <img :src="country.flag" alt="country flag">
    <p>{{country.name}}</p>
    <p>{{country.capital}}</p>
    <p>{{country.population}}</p>
    <p>Languages: </p>
    <ul>
      <li v-for="(language, index) in country.languages">{{language.name}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'country-detail',
  props: ['country']
}
</script>

<style lang="css" scoped>
img {
  max-width: 300px;
  padding: 1em;
  padding-left: 2em;
}
p {
  padding-left: 2em;
}
</style>
