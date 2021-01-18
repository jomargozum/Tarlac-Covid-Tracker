<template>
  <div class="column">
    <div class="card">
      <div class="card-content">
        <p class="title has-text-centered size">
          {{ title }}
        </p>
        <p class="subtitle  has-text-centered subsize">
          {{ cases }}
        </p>
      </div>
      <footer class="card-footer">
        <p class="card-footer-item">
          <span style="color:#F0C2CD;">
            As of {{ lastUpdated }}
          </span>
        </p>
      </footer>
    </div>
  </div>
</template>
<script>
export default {
  // eslint-disable-next-line vue/require-prop-types
  props: ['title', 'cases', 'lastUpdated']
}
</script>
<style scoped>
.size {
    font: bold 20px sans-serif;
    color: #FF4470;
}
.subsize {
    font: bold 70px sans-serif;
}
</style>
