<template>
  <div class="container">
    <div class="row card-group">
      <!-- BEER LIST -->
      <BeerList></BeerList>
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

    }
  },
  mounted () {

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
