<template>
  <div class="home mt-10 ">
    <div class="flex flex-col items-center">
    <homepage msg="Welcome to SOMCHAI CAFE"/>
    <img src="https://pbs.twimg.com/media/EO3G1bDUYAAwnNj.jpg" alt="hi" class=""/>
    </div>
  </div>
  <div id="btn" class="text-center mt-10" >
     <router-link to="/store" class="bg-blue-500 w-26 h-10 p-4 text-sm font-bold tracking-wider text-white rounded-full hover:bg-blue-600 inline-flex items-center justify ">Go to store</router-link>
  </div>
</template>


<script>
import Homepage from '@/components/Homepage.vue'


export default {
  name: 'home',
  components: {
    Homepage   
  }
}
</script>
