<template>
  <div>
    <div class="container">
      <div style="float: left"><b-button variant="outline-dark" size="sm" class="refresh"
          @click="refresh()">Refresh</b-button></div>
      <div style="float: right" >total: {{ markers.length }}</div>
      <div style="clear: both;"></div>

      <LeafletMap :markers="markers" :zoom="zoom"/>
    </div>
  </div>
</template>


<script>
// @ is an alias to /src
import LeafletMap from '@/components/LeafletMap.vue'

export default {
  name: 'SearchView',
  components: {
    LeafletMap
  },
  data() {
    return {

      /**
       * Coordinates API
       */
      apiCoordinates: "http://" + location.hostname + ":" + process.env.VUE_APP_LOCAL_PROXY_PORT + process.env.VUE_APP_API_COORDINATES,

      /**
       * Map zoom
       */
      zoom : 7,

      markers: [
        // {
        //   lat: 50.08476746164984,
        //   lng: 18.97534475266365,
        // },
        // {
        //   lat: 50.08167771832807,
        //   lng: 18.985255631312956,
        // },
      ],
    };
  },
  mounted() {
    //
  },
  methods: {
    async refresh() {

      const request = {
        method: "GET",
        headers: {
          "Accept": "application/json",
          "Content-Type": "application/json",
        },
        mode: "cors"
      };

      fetch(this.apiCoordinates, request)
        .then(async response => {
          const data = await response.json();
          this.markers = data;
          this.errorMessage = "";
        }).catch(error => {
          this.errorMessage = "There was an error while getting coordinates" + error;
        })

    },
  }
}
</script>

<style scoped>
.container {
  width: 50vw;
  margin-top: 10px;
}

.refresh {
  margin-bottom: 2px;
  border: 1px solid #fff;
  border-bottom: 2px solid #343A40;

}

</style>


