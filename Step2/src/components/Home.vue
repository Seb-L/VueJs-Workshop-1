<template>
  <div class="container">
    <div class="row card-group">

      <!-- BEER LIST -->
      <BeerList :beers="beers" v-model="selectedBeer"></BeerList>
    </div>
  </div>
</template>

<script>
import BeerList from './BeerList'

export default {
  name: 'home',
  data () {
    return {
      beers: []
    }
  },
  mounted () {
    this.axios.get('https://api.punkapi.com/v2/beers', { params: { per_page: 80 } })
      .then(({data}) => {
        this.beers = data
      })
  },
  components: {
    BeerList
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.beers-list{
  min-height: 500px;
}
</style>
