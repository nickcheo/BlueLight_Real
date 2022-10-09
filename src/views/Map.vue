<template>
  <div class="hello">
    <br>
    <h1 v-if="!awesome">Here is a map of all the emergency blue lights!</h1>
    <h1 v-else>Here is the closest emergency light to you!</h1>
   
  
      <b-button class="btn btn-outline mr-3" @click="findRoute(), awesome = true" style="background-color:rgb(141, 188, 212)">Find Nearest One</b-button>
    
      <b-button @click="resetMap(), awesome = false" style="background-color:rgb(141, 188, 212)">Reset Map</b-button>
   
    
    
    
    <br>    
    <br>
    <div id="myMap" style="height:715px; width:75%; margin:auto; border:2px solid black"></div>
    <br>
    <br>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Here is a map of all the emergency blue lights!',
      awesome: false
    }},
  mounted: function() {
        console.log("map: ", google.maps)
            this.map = new google.maps.Map(document.getElementById('myMap'), {
            center: {lat:39.9999, lng: -83.0122677},
            scrollwheel: false,
            zoom: 16,
            })
            new google.maps.Marker({
              position: new google.maps.LatLng(39.9990154, -83.0109998),
              map: this.map,
            })
            new google.maps.Marker({
              position: new google.maps.LatLng(39.9969632, -83.0094582),
              map: this.map,
            })
            new google.maps.Marker({
              position: new google.maps.LatLng(39.9994592, -83.0098022),
              map: this.map,
            })
            new google.maps.Marker({
              position: new google.maps.LatLng(40.0043908, -83.0091599),
              map: this.map,
            })
            new google.maps.Marker({
              position: new google.maps.LatLng(39.9981465, -83.0079833),
              map: this.map,
            })
            new google.maps.Marker({
              position: new google.maps.LatLng(40.0022517, -83.0086039),
              map: this.map,
            })
            new google.maps.Marker({
              position: new google.maps.LatLng(40.0038071, -83.0042611),
              map: this.map,
            })
            new google.maps.Marker({
              position: new google.maps.LatLng(40.0028401, -83.0032070),
              map: this.map,
            })
            new google.maps.Marker({
              position: new google.maps.LatLng(40.0011286, -83.0037149),
              map: this.map,
            })
            new google.maps.Marker({
              position: new google.maps.LatLng(39.9997826, -83.0036693),
              map: this.map,
            })
            new google.maps.Marker({
              position: new google.maps.LatLng(39.9984845, -83.0013486),
              map: this.map,
            });
        
            // this.marker = new google.maps.Marker({
            //  position: new google.maps.LatLng(19.373341, 78.662109),
            //  map: myMap,
            //  });
  },
  methods: {
    resetMap() {
      this.map = new google.maps.Map(document.getElementById('myMap'), {
            center: {lat:39.9999, lng: -83.0122677},
            scrollwheel: false,
            zoom: 15,
            })
            new google.maps.Marker({
              position: new google.maps.LatLng(39.9990154, -83.0109998),
              map: this.map,
            })
            new google.maps.Marker({
              position: new google.maps.LatLng(39.9969632, -83.0094582),
              map: this.map,
            })
            new google.maps.Marker({
              position: new google.maps.LatLng(39.9994592, -83.0098022),
              map: this.map,
            })
            new google.maps.Marker({
              position: new google.maps.LatLng(40.0043908, -83.0091599),
              map: this.map,
            })
            new google.maps.Marker({
              position: new google.maps.LatLng(39.9981465, -83.0079833),
              map: this.map,
            })
            new google.maps.Marker({
              position: new google.maps.LatLng(40.0022517, -83.0086039),
              map: this.map,
            })
            new google.maps.Marker({
              position: new google.maps.LatLng(40.0038071, -83.0042611),
              map: this.map,
            })
            new google.maps.Marker({
              position: new google.maps.LatLng(40.0028401, -83.0032070),
              map: this.map,
            })
            new google.maps.Marker({
              position: new google.maps.LatLng(40.0011286, -83.0037149),
              map: this.map,
            })
            new google.maps.Marker({
              position: new google.maps.LatLng(39.9997826, -83.0036693),
              map: this.map,
            })
            new google.maps.Marker({
              position: new google.maps.LatLng(39.9984845, -83.0013486),
              map: this.map,
            });
    },
      
      findRoute() {
        var longitude = 0;
        navigator.geolocation.getCurrentPosition(
          position => {
            this.lastResort(position.coords.latitude, position.coords.longitude);
            
          },
          error => {
            console.log(error.message);
          },
        )
        // var position =  this.getPosition();
        
        // position.then(values => {
        //   console.log(values[1]);
        // });
        // this.getLocation();

        console.log("am I even here right now")
        console.log(longitude);
        this.map = new google.maps.Map(document.getElementById('myMap'), {
            center: {lat:39.9999, lng: -83.0122677},
            scrollwheel: false,
            zoom: 15,
            })
        // new google.maps.Marker({
        //   position: new google.maps.LatLng(39.9984845, -83.0013486),
        //   map: this.map,
        //   });
        const directionsService = new google.maps.DirectionsService();
        const directionsRenderer = new google.maps.DirectionsRenderer();
        directionsService.route({
          // origin: '156 E 13th Ave Columbus, OH 43210',
          origin: { lat: 0, lng: longitude },
          destination: { lat: 39.9984845, lng: -83.0013486},
          // destination: '1739 N High St, Columbus, OH 43210',
          travelMode: "WALKING"
        },
        (response, status) => {
          if (status === "OK") {
            directionsRenderer.setDirections(response);
            directionsRenderer.setMap(this.map);
          }
          console.log(response);
          console.log(status);

        }
        
        );
      },
      lastResort(lat, lng) {
        const array = [[39.9990154, -83.0109998], [39.9969632, -83.0094582], [39.9994592, -83.0098022], [40.0043908, -83.0091599], [39.9981465, -83.0079833], [40.0022517, -83.0086039],[40.0038071, -83.0042611],[40.0028401, -83.0032070],[40.0011286, -83.0037149], [39.9997826, -83.0036693],[39.9984845, -83.0013486]];
        array.sort();
        var min = array[0];
        var minDist = 100000, currentDist = 0;
        for(let i = 0; i<array.length; i++){
          currentDist = Math.sqrt(Math.pow((array[i][0] - lat), 2) + Math.pow((array[i][1] - lng), 2));
          if (currentDist < minDist){
            minDist = currentDist;
            min = array[i]
          }
          

        }
        this.map = new google.maps.Map(document.getElementById('myMap'), {
            center: {lat:39.9999, lng: -83.0122677},
            scrollwheel: false,
            zoom: 16,
            })
        const directionsService = new google.maps.DirectionsService();
        const directionsRenderer = new google.maps.DirectionsRenderer();
        directionsService.route({
          // origin: '156 E 13th Ave Columbus, OH 43210',
          // origin: { lat: lat, lng: lng },
          origin: { lat: lat, lng: lng },
          destination: { lat: min[0], lng: min[1]},
          // destination: '1739 N High St, Columbus, OH 43210',
          travelMode: "WALKING"
        },
        (response, status) => {
          if (status === "OK") {
            directionsRenderer.setDirections(response);
            directionsRenderer.setMap(this.map);
          }
          console.log(response);
          console.log(status);

        }
        );
      }
      
      

  }

  }


</script>
<style scoped>
    #myMap {
    height:300px;
    width: 100%;
   }
   .hello {
    background-color: rgb(225, 225, 221);
   }
</style>

<!-- <template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button @click="findRoute()">Find Route</button>
    <div id="myMap"></div>
  </div>
</template>
<script>


export default{
    name: 'hello',
    data() {
        return {
          map: null,
          mapCenter: {lat:39.999, lng:83.0122677}
        }
    },
    methods: {
      // initMap() {
      //   console.log("map: ", google.maps)
      //       this.map = new google.maps.Map(document.getElementById('myMap'), {
      //           center: this.mapCenter,
      //           scrollwheel: false,
      //           zoom: 16,
      //       })
      findRoute() {
        console.log("am I even here right now")
        this.map = new google.maps.Map(document.getElementById('myMap'), {
            center: {lat:39.9999, lng: -83.0122677},
            scrollwheel: false,
            zoom: 16,
            })
      }
      
    }
    // mounted: function() {
    //     console.log("map: ", google.maps)
    //         this.map = new google.maps.Map(document.getElementById('map'), {
    //             center: {lat:39.9999, lng: -83.0122677},
    //             scrollwheel: false,
    //             zoom: 16,
    //         })
    // },
    // mounted() {
    //     this.initMap()
    // }
}
</script> -->
