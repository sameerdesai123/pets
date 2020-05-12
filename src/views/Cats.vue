<template>
    <PetTable
    species="cats"
    :pets="cats"
    :fields="fields"
    />
</template>

<script>
import { mapState } from 'vuex'
import PetTable from '@/components/PetTable.vue'

export default {
  name: 'Cats',
  components: {
    PetTable
  },
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
