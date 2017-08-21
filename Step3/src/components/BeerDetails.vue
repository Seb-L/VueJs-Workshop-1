<template>
  <div class="col-6 card pt-4">

    <!-- BEER SELECTED -->
    <div class="card-body">
      <div class="row">
        <div class="col-3 text-center">
          <img :src="beer.image_url" class="img-responsive" height="150">
        </div>
        <div class="col">
          <h3>{{ beer.name }}</h3>
          <h6 class="card-subtitle mb-2 text-muted">{{ beer.tagline }}</h6>
          <p><strong>Deg:</strong> {{ beer.abv }}°</p>
          <p>
            <strong>Food Pairing:</strong> {{ beer.food_pairing.join(', ') }}
          </p>
        </div>
      </div>
      <br>
      <p>
        <strong>Description:</strong><br>
        {{ beer.description }}
      </p>
      <p>
        <strong>Brewers Tips:</strong><br>
        {{ beer.brewers_tips }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BeerDetails',
  props: ['beer']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.beers-list{
  min-height: 500px;
}
</style>
