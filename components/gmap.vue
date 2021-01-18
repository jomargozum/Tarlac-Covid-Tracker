<template>
  <div class="column is-four-fifths">
    <div>
      <div class="has-text-weight-large">
        <h1>
          Maps
        </h1>
      </div>

      <gmap-map :center="center" :map-type-id="mapTypeId" :zoom="10">
        <gmap-marker
          v-for="(item, index) in markers"
          :key="index"
          :position="item.position"
          :icon="markerOptions"
          @click="center = item.position"
        />
        />
      </gmap-map>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    const mapMarker = require('~/assets/covid-virus.png')
    return {
      markerOptions: {
        url: mapMarker,
        scaledSize: { width: 70, height: 60, f: 'px', b: 'px' }
      },
      center: { lat: 15.487695, lng: 120.596764 },
      mapTypeId: 'terrain',
      markers: [
        { position: { lat: 15.607589, lng: 120.593499 } },
        { position: { lat: 15.644692, lng: 120.572548 } },
        { position: { lat: 15.332138, lng: 120.589002 } },
        { position: { lat: 15.440510, lng: 120.607059 } },
        { position: { lat: 15.687433, lng: 120.416201 } },
        { position: { lat: 15.459259, lng: 120.590707 } },
        { position: { lat: 15.272385, lng: 120.564946 } },
        { position: { lat: 15.687649, lng: 120.416136 } },
        { position: { lat: 15.694773, lng: 120.459107 } },
        { position: { lat: 15.475095, lng: 120.596403 } },
        { position: { lat: 15.687414, lng: 120.579854 } },
        { position: { lat: 15.594596, lng: 120.657778 } },
        { position: { lat: 15.297081, lng: 120.539798 } },
        { position: { lat: 15.689486, lng: 120.405192 } },
        { position: { lat: 15.495944, lng: 120.602729 } },
        { position: { lat: 15.383929, lng: 120.590525 } },
        { position: { lat: 15.330692, lng: 120.641079 } },
        { position: { lat: 15.498038, lng: 120.598901 } },
        { position: { lat: 15.651532, lng: 120.409593 } },
        { position: { lat: 15.325272, lng: 120.590588 } }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
.vue-map-container {
  height: 450px;
  max-width: 992px;
  width: 100%;
}

</style>
