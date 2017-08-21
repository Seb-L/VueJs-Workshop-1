<template>
  <button
    @click="$emit('selectBeer', beer)"
    class="list-group-item list-group-item-action"
    :disabled="selectedBeer && selectedBeer.id === beer.id">

    <h5>{{ beer.name }}</h5>
    <h6 class="text-muted">{{ beer.tagline }}</h6>
  </button>
</template>

<script>
export default {
  name: 'BeerItem',
  props: ['beer', 'selectedBeer']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
