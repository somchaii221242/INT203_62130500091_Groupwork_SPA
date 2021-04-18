<template>
<div class="store bg-red-100"> 
   
  <div class="bg-image w-full min-h-screen flex flex-wrap justify-center items-center gap-3 py-5">
    <div class="backdrop w-10/12 md:w-1/4 bg-white bg-opacity-10 rounded p-3 text-white border border-gray-300 shadow-lg">
      <!-- header -->
      <div class="w-full mb-3 pb-3 border-b border-1 border-white">
        <h3 class="text-black  text-xl font-semibold text-shadow">Milk</h3>
      </div>
      <!-- body -->
      <div>
        <img src="https://gf.lnwfile.com/eu1pip.jpg" alt="image1" class="w-full h-48 object-cover mb-2">
      </div>
    </div>
    <div class="backdrop w-10/12 md:w-1/4 bg-white bg-opacity-10 rounded p-3 text-white border border-white shadow-lg">
      <!-- header -->
      <div class="w-full mb-3 pb-3 border-b border-1 border-white">
        <h3 class="text-black text-xl font-semibold text-shadow">Green Tea</h3>
      </div>
      <!-- body -->
      <div>
        <img src="@/assets/greentea.jpg" alt="image2" class="w-full h-48 object-cover mb-2">
      </div>
    </div>
    <div class="backdrop w-10/12 md:w-1/4 bg-white bg-opacity-10 rounded p-3 text-white border border-white shadow-lg">
      <!-- header -->
      <div class="w-full mb-3 pb-3 border-b border-1 border-white">
        <h3 class="text-black text-xl font-semibold text-shadow">Americano</h3>
      </div>
      <!-- body -->
      <div>
        <img src="@/assets/americano.jpg/" alt="image3" class="w-full h-48 object-cover mb-2">
      </div>
    </div>
  </div>
  

</div>


</template>

<script>
export default {
  name: "store",
  props: {
    msg: String,
  },
};
</script>
<style>

    .backdrop {
      backdrop-filter: blur(5px);
    }
    .text-shadow {
      text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.3);
    }
  </style>