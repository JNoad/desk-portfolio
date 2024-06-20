<template>
    <NavBar/>
    <router-view/>
</template>

<script>
import NavBar from "@/components/NavBar.vue";
export default {
    components: {
        NavBar
    }
}
</script>

<style>
* {
    box-sizing: border-box;
    padding: 0;
    margin: 0;
}
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    background-image: url(https://www.desktopbackground.org/download/1600x900/2015/11/20/1044959_wood-panel-hd-backgrounds-bible-clipart_1600x1200_h.jpg);
    height: 100vh;
}
</style>
