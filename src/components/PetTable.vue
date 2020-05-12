<template>
    <div>
      <h1>{{ species }}</h1>
      <b-table striped hover :items="pets" :fields="fields">
        <template v-slot:cell(name)="data">
        <!-- `data.value` is the value after formatted by the Formatter -->
        <router-link :to="`/pets/${species}/${data.index}`">
        {{ data.value }}
        </router-link>
      </template>
      </b-table>
  </div>
</template>

<script>
export default {
  props: {
    species: String,
    pets: Array,
    fields: Array
  }
}
</script>
