<template>
  <div>
      <h1>Dogs</h1>
      <b-table striped hover :items="dogs" :fields="fields">
        <template v-slot:cell(name)="data">
        <!-- `data.value` is the value after formatted by the Formatter -->
        <router-link :to="`/pets/dogs/${data.index}`">
        {{ data.value }}
        </router-link>
      </template>
      </b-table>
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {
  name: 'Dogs',
  data () {
    return {
      fields: ['name', 'age', 'sound', 'price']
    }
  },
  computed: mapState({
    dogs: state => state.dogs
  })
}
</script>

<style scoped>

</style>
