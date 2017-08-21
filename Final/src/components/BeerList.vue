<template>
  <div class="col card bg-light col-6">
    <!-- FILTER -->
    <div class="form-group card-header row">
      <input type="text" v-model="searchTerms" placeholder="Filter beers by name" class="form-control">
    </div>

    <div class="beers-list list-group pt-3 pb-3">
      <!-- LOADING BEERS -->
      <p v-if="beersLoading">Loading beers...</p>

      <!-- BEER LIST -->
      <button
        v-for="beer in paginatedBeers"
        :key="beer.id"
        @click="$emit('input', beer)"
        :disabled="value && value.id === beer.id"
        class="list-group-item list-group-item-action">

        <h5>{{ beer.name }}</h5>
        <h6 class="text-muted">{{ beer.tagline }}</h6>
      </button>

      <!-- NO BEERS IN FILTERED LIST -->
      <p v-if="!paginatedBeers.length && !beersLoading">
        No beer found
      </p>
    </div>

    <!-- PAGINATE -->
    <div class="card-footer row">
      <ul class="pagination pagination-sm justify-content-center">
        <li v-for="page in pagesAmount" class="page-item" :class="{ 'active': currentPage === page }">
          <a class="page-link" @click="currentPage = page">{{ page }}</a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BeerList',
  props: ['beers', 'value'],
  data () {
    return {
      searchTerms: '',
      beerPerPage: 6,
      currentPage: 1
    }
  },
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
    },
    paginatedBeers () {
      const from = (this.currentPage - 1) * this.beerPerPage
      const to = this.currentPage * this.beerPerPage
      return this.filteredBeers.slice(from, to)
    },
    pagesAmount () {
      return Math.ceil(this.filteredBeers.length / this.beerPerPage)
    }
  },
  watch: {
    searchTerms () {
      this.currentPage = 1
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
