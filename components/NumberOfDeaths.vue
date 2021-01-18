<template>
  <div class="has-text-centered is-size-1 has-text-danger has-text-weight-bold">
    <h5 style="font-weight:bold">
      Deaths - {{ num }}
    </h5>
  </div>
</template>
<script>
export default {
  // eslint-disable-next-line vue/require-prop-types
  props: ['num']
}
</script>
