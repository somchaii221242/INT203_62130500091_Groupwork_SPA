<template>
  <div id="nav" class="text-center bg-gray-500 h-12">
    <router-link to="/home" id="home">Home</router-link> 
    <router-link to="/store" id="store">Store</router-link> 
    <router-link to="/about" id="about">About</router-link>
  </div>
  <router-view/>
</template>

<style>
#home{
  padding: 50px;
}
#about{
  padding: 50px;
}
</style>