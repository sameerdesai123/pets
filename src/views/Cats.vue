<template>
    <div>
      <h1>Cats</h1>
      <b-table striped hover :items="cats" :fields="fields">
        <template v-slot:cell(name)="data">
        <!-- `data.value` is the value after formatted by the Formatter -->
        <router-link :to="`/pets/cats/${data.index}`">
        {{ data.value }}
        </router-link>
      </template>
      </b-table>
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {
  name: 'Cats',
  data () {
    return {
      fields: ['name', 'age', 'sound', 'price']
    }
  },
  computed: mapState({
    cats: state => state.cats
  })
}
</script>

<style scoped>

</style>
