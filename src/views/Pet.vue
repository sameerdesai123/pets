<template>
    <div>
      {{ $route.params.species }}
      {{ $route.params.id }}
    </div>
</template>

<script>
export default {
  name: 'Pet'
}
</script>

<style scoped>

</style>
