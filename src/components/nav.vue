<template>
   <div>
    <v-app-bar
    app
    color="white"
    dark
    >
     <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="../assets/wifinity/wifinity-NEW.png"
          transition="scale-transition"
          width="100"
          height="40"
        />
        <div class="tabs">
            <ul>
         <li><a id="nav-link">Features</a></li>
        <li><a id="nav-link">Resources</a></li>
        <li><a id="nav-link">Pricing</a></li>
            </ul>
 
            

        </div>
        <v-spacer></v-spacer>
        <v-btn color="#1D0C42">SignIn</v-btn>
        
    </v-app-bar>
   </div>
</template>
<script>
export default {
    
}
</script>
<style scoped>
 .tabs li {
    float:left;
    list-style-type: none;
    color: black;
    padding:80px
  }
   #nav-link:hover{
      color:purple;
      text-decoration:none
  }
  .tabs a {
      color: black;
      text-align: center;
      padding: 20px;
      text-decoration: none;
      display: block;
      
  }
  
  

</style>