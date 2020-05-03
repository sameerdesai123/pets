<template>
    <b-container class="bv-example-row">
  <b-row>
    <b-col class="sm-6" offset=3>
      <b-card
        :title=animal.name
        :img-src=animal.src
        img-alt="Image"
        img-bottom
        tag="article"
        style="max-width: 20rem;"
        class="mb-2"
  >
    <b-card-text>
      {{ animal.name}} is {{ animal.age }} years old and does {{ animal.sound }} at just {{ animal.price }}.
    </b-card-text>

    <router-link :to="`/${$route.params.species}`"><b-button variant="primary">All {{ $route.params.species }}</b-button></router-link>
  </b-card>
    </b-col>
  </b-row>
</b-container>
</template>

<script>
import { mapState } from 'vuex'

export default {
  name: 'Pet',
  data () {
    return {
      animal: {}
    }
  },
  computed: mapState({
    cats: state => state.cats,
    dogs: state => state.dogs
  }),
  mounted () {
    const animal = this[this.$route.params.species][this.$route.params.id]
    this.animal = animal
  }
}
</script>

<style scoped>

</style>
