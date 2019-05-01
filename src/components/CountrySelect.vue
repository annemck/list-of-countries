<template lang="html">
  <div>
    <select v-on:change="handleSelect" v-model="country">
      <option v-for="(country, index) in countries" :key="index" :value="country">{{country.name}}</option>
    </select>
  </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
  name: 'country-select',
  data(){
    return {
      country: null
    }
  },
  props: ['countries'],
  methods: {
    handleSelect: function(){
      eventBus.$emit('selected-country', this.country);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
