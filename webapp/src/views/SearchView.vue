<template>
<div >
    <div class="container rounded">
      <MarkerMap :markers="markers" />
    </div>
</div>
</template>


<script>
// @ is an alias to /src
import MarkerMap from '@/components/MarkerMap.vue'

export default {
  name: 'SearchView',
  components: {
    MarkerMap
  },
  data() {
    return {
      markers: [
        {
          position: {
            lat: 50.08476746164984,
            lng: 18.97534475266365,
          },
        },
        {
          position: {
            lat: 50.08167771832807, 
            lng: 18.985255631312956,
          },
        },
        {
          position: {
            lat: 50.07090064441086, 
            lng: 18.997151613185807,
          },
        },
      ],
    };
  },
}
</script>

<style scoped>
  .container{
    width: 50vw;
    margin: auto;
    background-color: red;
    padding: 10px;
    margin-top: 10px;
  }
</style>
