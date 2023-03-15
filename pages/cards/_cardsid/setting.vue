<template>
  <h1>Trang setting{{ $route.params.cardsid }}</h1>
</template>

<script>
export default {
  name: 'PageSetting',
  computed: {
    ...mapState( [
    ]),
    ...mapState('store', {
      axamHEHE: (state) => state.propState
    }),
  }
}
</script>

<style>

</style>
