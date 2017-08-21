<template>
  <div class="col card bg-light col-6">
    <div class="beers-list list-group pt-3 pb-3">
      <!-- LOADING BEERS -->
      <p v-if="beersLoading">Loading beers...</p>

      <!-- BEER LIST -->
      <button
        v-for="beer in filteredBeers"
        :key="beer.id"
        :disabled="value && value.id === beer.id"
        class="list-group-item list-group-item-action">

        <h5>{{ beer.name }}</h5>
        <h6 class="text-muted">{{ beer.tagline }}</h6>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BeerList',
  props: ['beers', 'value'],
  computed: {
    beersLoading () {
      return !this.beers.length && !this.searchTerms
    },
    filteredBeers () {
      return this.beers
        .filter(beer => {
          return this.searchTerms ? beer.name.toLowerCase().includes(this.searchTerms.toLowerCase()) : true
        })
        .sort((a, b) => {
          if (a.name < b.name) {
            return -1
          } else if (a.name > b.name) {
            return 1
          } else {
            return 0
          }
        })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.beers-list{
  min-height: 500px;
}
</style>
