<template>
  <div id="Home" class="w-screen min-h-screen flex flex-row bg-white">
    <div class="overflow-y-auto basis-5/12 h-screen flex flex-col">
    <div class="my-6">
        <img :src="detailLoc.Images[0].imageUrl" alt="" srcset="">
      </div>
    <div class="my-24">
        <p
          class="text-6xl px-6"
          style="font-family: 'Encode Sans', sans-serif; font-weight: 700"
        >
          {{ detailLoc.name }}
        </p>
      </div>
    <h1 class="px-8">{{detailLoc.address}}</h1>
    <h1>{{detailLoc.price}}</h1>
    <a class="rounded-full bg-green-500 py-6 px-12 text-white text-3xl" :href="detailLoc.mapsUrl">Go to Google Map</a>
    </div>
    <div class="basis-7/12 h-screen">
      <gmap-map
        :zoom="18"
        :center="detailCenter"
        :options="options"
        style="width: 100%; height: 100%"
      >
        <gmap-marker
          :position="detailCenter"
          :clickable="false"
          :draggable="false"
        ></gmap-marker>
      </gmap-map>
    </div>
  </div>
</template>

<script>
import { mapState } from 'vuex'
// import GoogleMaps from '../components/GoogleMaps.vue'


export default {
  name: 'LocationDetail',
  components: {
    // GoogleMaps
  },
  data() {
    return {
      options: {
        fullscreenControl: false,
      },
    }
  },
  computed: {
    ...mapState(['detailLoc']),
    detailCenter() {
      return {
        lat: +this.detailLoc.lattitude,
        lng: +this.detailLoc.longitude
      }
    }
  }
}
</script>
