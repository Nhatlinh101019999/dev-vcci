<template>
  <div class=" mx-auto bg-img ">
    <div class="flex justify-center">
      <HeaderNuxt/>
    </div>
  </div>
</template>
<script>

// import styles bundle

import HeaderNuxt from '~/components/Header/HeaderNuxt.vue'

export default {
  name: 'IndexPage',
  components: { HeaderNuxt }

  // Events
}
</script>
<style scoped>
.bg-img {
    background-image: url("https://vcci-erp.vn/img/vuexy-login-bg.04351a33.jpg");
    background-position: 50%;
    background-repeat: repeat-y;
    background-size: cover;
}
</style>
