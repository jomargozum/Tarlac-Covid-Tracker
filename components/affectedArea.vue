<template>
  <div class="column is-half">
    <div class="card">
      <div class="card-content">
        <p class="title has-text-centered size">
          {{ area }}
        </p>
        <p class="subtitle  has-text-centered subsize">
          No. of Cases: {{ cases }}
        </p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  // eslint-disable-next-line vue/require-prop-types
  props: ['area', 'cases']
}
</script>
<style lang="scss" scoped>

.size {
    font: bold 20px sans-serif;
    color: #FF4470;
}
</style>
