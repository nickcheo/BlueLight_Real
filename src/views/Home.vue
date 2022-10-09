<template>
  <div class="home" :style="{backgroundImage: 'url(' + require('@/assets/history.jpg') + ')' }">
     
   
    <div class="row main-row align-items-center">
    <div class="container-fluid" style="height:900px">
      
          
                  <h1 style="font-size:100px; padding-top: 10%; color:black;"><strong >Blue Light</strong></h1>
                    <p style="font-size:35px; color:black;">A way to track emergency blue light boxes at The Ohio State University.</p>
                    <!-- <button @click="$router.push('about')">Click to Navigate</button> -->
                    <b-button @click="$router.push('map')">Go to Emergency Light Map</b-button>
                    <br>
                    <!-- <div id = 'spin-box'>
                    </div> 
                    <div id = 'check-box'></div> -->
                    
                  
            
           

                  

                    
                    <!-- <button type:"button" class="btn btn-primary">Connect with Spotify</button> -->
                      <!--Button-->
                </div>
              </div>
              
            </div>
    
       
       
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import HelloWorld from "../components/HelloWorld.vue"; // @ is an alias to /src

@Component({
  components: {
    HelloWorld,
  },
})
export default class Home extends Vue {}
</script>

<style scoped>
.home2 {
  font-size: 25px;
}
.fill { 
  min-height: 100%;
  height: 100%;
}
</style>