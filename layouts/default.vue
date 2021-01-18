<template>
  <div class="bg">
    <disclaimer />
    <navbar />
    <nuxt />
    <mainFooter />
  </div>
</template>
<script>
import navbar from '~/components/mainNav'
import disclaimer from '~/components/disclaimer'
import mainFooter from '~/components/footer'
export default {
  components: {
    navbar,
    disclaimer,
    mainFooter
  }
}
</script>
<style scoped>
.bg{
  background-color:#FFF5F5;
}
</style>
