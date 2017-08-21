<template>
  <div class="container">
    <div class="row card-group">
      <div class="col card bg-light col-6">
        <div class="beers-list list-group pt-3 pb-3">
          <!-- LOADING BEERS -->
          <p v-if="!beersLoaded">Loading beers...</p>

          <!-- BEER LIST -->
          <BeerItem
            v-for="beer in beers"
            :key="beer.id"
            :beer="beer"
            :selectedBeer="selectedBeer"
            @selectBeer="selectBeer">
          </BeerItem>

          <!-- NO BEERS IN FILTERED LIST -->
          <p v-if="!paginatedBeers.length && beersLoaded">
            No beer found
          </p>
        </div>
      </div>

      <!-- SELECTED BEER DETAILS -->
      <BeerDetails v-if="selectedBeer" :beer="selectedBeer"></BeerDetails>
    </div>
  </div>
</template>

<script>
import BeerItem from './BeerItem.vue'
import BeerDetails from './BeerDetails.vue'

export default {
  name: 'home',
  data () {
    return {
      beersLoaded: false,
      beers: [],
      selectedBeer: null
    }
  },
  methods: {
    selectBeer (beer) {
      this.selectedBeer = beer
    }
  },
  mounted () {
    this.axios.get('https://api.punkapi.com/v2/beers', { params: { per_page: 80 } })
      .then(({data}) => {
        this.beers = data
        this.beersLoaded = true
      })
  },
  components: {
    BeerItem,
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
