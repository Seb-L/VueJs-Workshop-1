<template>
  <div class="col card bg-light col-6">
    <div class="beers-list list-group pt-3 pb-3">
      <!-- LOADING BEERS -->
      <p v-if="beersLoading">Loading beers...</p>

      <!-- BEER LIST -->
      <button
        v-for="beer in beers"
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
      return !this.beers.length
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
