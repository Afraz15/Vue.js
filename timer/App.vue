<template>
    <div id="app" class="card shadow-lg ">
        <Count />
    </div>
</template>

<script>

import Count from "./components/Counter"
import Head from "./components/Header"

export default { 
    name: "App",
    components: {
        Count,
    }
}


</script>

<style scoped>

#app{
    text-align: center;
    padding: 8rem;
    margin: 12rem 8rem 0 8rem;
    background-image: url('https://cutewallpaper.org/21/black-background-1920x1080/79-1080P-Black-Wallpapers-on-WallpaperPlay.jpg');
    color: whitesmoke;
}



</style>

