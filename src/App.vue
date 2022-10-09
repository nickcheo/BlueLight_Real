<template>
<div id="app"> 
    <div>
        <b-navbar toggleable="lg" variant="dark" type="dark">
          <b-navbar-brand><router-link to="/" style="color:black">Blue Light</router-link></b-navbar-brand>
      
          <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
      
          <b-collapse id="nav-collapse" is-nav>
            <b-navbar-nav>
                <!-- <router-link to="/">Home</router-link> -->
              <b-nav-item><router-link to="/" style="color:black">Home</router-link></b-nav-item>
              <b-nav-item><router-link to="/about" style="color:black">About</router-link></b-nav-item>
              <b-nav-item><router-link to="/map" style="color:black">Map</router-link></b-nav-item>
            </b-navbar-nav>
      
            <!-- Right aligned nav items -->
            <!-- <b-navbar-nav class="ml-auto">
              <b-nav-form>
                <b-form-input size="sm" class="mr-sm-2" placeholder="Search"></b-form-input>
                <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
              </b-nav-form>
      
              <b-nav-item-dropdown text="Lang" right>
                <b-dropdown-item href="#">EN</b-dropdown-item>
                <b-dropdown-item href="#">ES</b-dropdown-item>
                <b-dropdown-item href="#">RU</b-dropdown-item>
                <b-dropdown-item href="#">FA</b-dropdown-item>
              </b-nav-item-dropdown>
      
              <b-nav-item-dropdown right> -->
                <!-- Using 'button-content' slot -->
                <!-- <template #button-content>
                  <em>User</em>
                </template>
                <b-dropdown-item href="#">Profile</b-dropdown-item>
                <b-dropdown-item href="#">Sign Out</b-dropdown-item> -->
              <!-- </b-nav-item-dropdown> -->
            <!-- </b-navbar-nav> -->
          </b-collapse>
        </b-navbar>
      </div>

    <router-view/>
    <!-- <div v-if="this.$route.path == '/about'">
        <router-view/> -->
</div>
    <!-- <b-button @click="goToAbout()">Button</b-button> -->
    
    
<!-- </div> -->
</template>

<script>

export default {
    name: 'App',
    methods: {
        
        goToAbout(){
        this.$router.push('/about');
        
    }
    }
    
}



</script>
<style scoped>
#app {
    
    
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
}
.navbar.navbar-dark.bg-dark{
  background-color: rgb(141, 188, 212)!important;
}
</style>