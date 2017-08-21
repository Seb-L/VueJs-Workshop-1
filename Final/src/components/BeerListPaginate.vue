<template>
  <div class="card-footer row">
    <ul class="pagination pagination-sm justify-content-center">
      <li v-for="page in pagesAmount" class="page-item" :class="{ 'active': currentPage === page }">
        <a class="page-link" @click="currentPage = page">{{ page }}</a>
      </li>
    </ul>
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
      searchTerms: '',
      beerPerPage: 6,
      currentPage: 1,
      selectedBeer: null
    }
  },
  computed: {
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
