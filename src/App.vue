<template>
    <div id="app">
        <div id="nav">
            <router-link to="/">Home</router-link> |
            <router-link to="/board">Board</router-link> |
            <!-- <router-link to="firstquarter.tistory.com">Blog</router-link> -->
            <a
                href="https://firstquarter.tistory.com"
                target="blank"
            >Blog</a>
        </div>
        <router-view />
    </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
    name: "App",
    mounted() {
        console.log(
            `%c안%c녕 %c난 %c프%c론%c트%c야`,
            "color: red; font-style: italic; padding: 4px; border-radius: 4px; font-size: 88px",
            "color: orange; font-style: italic; padding: 4px; border-radius: 4px; font-size: 88px",
            "color: yellow; font-style: italic; padding: 4px; border-radius: 4px; font-size: 88px",
            "color: #9BFA73; font-style: italic; padding: 4px; border-radius: 4px; font-size: 88px",
            "color: #C0FFFF; font-style: italic; padding: 4px; border-radius: 4px; font-size: 88px",
            "color: #0000CD; font-style: italic; padding: 4px; border-radius: 4px; font-size: 88px",
            "color: violet; font-style: italic; padding: 4px; border-radius: 4px; font-size: 88px"
        );
        console.log(
            `%c                                                                                                                                                   

 .d8888b.                             888    888                            
d88P  Y88b                            888    888                            
Y88b.                                 888    888                            
 "Y888b.    8888b.  88888b.   .d88b.  8888888888 888  888 888  888 88888b.  
    "Y88b.     "88b 888 "88b d88P"88b 888    888 888  888 888  888 888 "88b 
      "888 .d888888 888  888 888  888 888    888 888  888 888  888 888  888 
Y88b  d88P 888  888 888  888 Y88b 888 888    888 Y88b 888 Y88b 888 888  888 
 "Y8888P"  "Y888888 888  888  "Y88888 888    888  "Y88888  "Y88888 888  888 
                                  888                 888                   
                             Y8b d88P            Y8b d88P                   
                              "Y88P"              "Y88P"                    

`,
            "color:#FFC3FA"
        );
        console.log(
            `%c

 .d8888b.                888          888              d8b          888      
d88P  Y88b               888          888              Y8P          888      
888    888               888          888                           888      
888         .d88b.   .d88888  .d88b.  88888b.  888d888 888  .d8888b 888  888 
888        d88""88b d88" 888 d8P  Y8b 888 "88b 888P"   888 d88P"    888 .88P 
888    888 888  888 888  888 88888888 888  888 888     888 888      888888K  
Y88b  d88P Y88..88P Y88b 888 Y8b.     888 d88P 888     888 Y88b.    888 "88b 
 "Y8888P"   "Y88P"   "Y88888  "Y8888  88888P"  888     888  "Y8888P 888  888 

`,
            "color:powderblue"
        );
    },
});
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}

#nav {
    padding: 30px;
}

#nav a {
    font-weight: bold;
    color: #2c3e50;
}

#nav a.router-link-exact-active {
    color: #42b983;
}
</style>
