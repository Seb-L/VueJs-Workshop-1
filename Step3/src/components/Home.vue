<template>
  <div class="container">
    <div class="row card-group">

      <!-- BEER LIST -->
      <BeerList :beers="beers" v-model="selectedBeer"></BeerList>

      <!-- SELECTED BEER DETAILS -->
      <BeerDetails v-if="selectedBeer" :beer="selectedBeer"></BeerDetails>
    </div>
  </div>
</template>

<script>
import BeerList from './BeerList'
import BeerDetails from './BeerDetails.vue'

export default {
  name: 'home',
  data () {
    return {
      beers: [],
      selectedBeer: null
    }
  },
  mounted () {
    this.axios.get('https://api.punkapi.com/v2/beers', { params: { per_page: 80 } })
      .then(({data}) => {
        this.beers = data
      })
  },
  components: {
    BeerList,
    BeerDetails
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.beers-list{
  min-height: 500px;
}
</style>
