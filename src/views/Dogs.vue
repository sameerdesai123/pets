<template>
    <PetTable
    species="dogs"
    :pets="dogs"
    :fields="fields"
    />
</template>

<script>
import { mapState } from 'vuex'
import PetTable from '@/components/PetTable.vue'
export default {
  name: 'Dogs',
  components: {
    PetTable
  },
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
