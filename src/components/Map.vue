<script>
const app = Vue.createApp({el: '#app', })    
		
app.component('map-component', {
  data() {
    return {
      map_red: false
    }
  }, 
  
  template: '<div id="map"></div><div><button v-on:click="make_red" v-if="!map_red">Make Red</button></div>',
  
  mounted: function(){
    simplemaps_usmap.load();
  },
  computed: {
    simplemaps_usmap: function () {return window.simplemaps_usmap;}
  },
  methods: {
    make_red: function(){
      this.map_red = true;
      simplemaps_usmap.mapdata.main_settings.state_color = 'red';
      simplemaps_usmap.refresh();
    }        
  }
})

app.mount("#components-demo");

</script>