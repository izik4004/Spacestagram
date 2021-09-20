<template>
  <Layout>
    <div>

<!-- component -->
<section class="text-gray-600 body-font">
  <div class="container px-5 py-24 mx-auto max-w-7x1">
    <div class="flex flex-wrap w-full p-4 mb-4">
      <div class="w-full mb-6 lg:mb-0">
        <h1 class="mb-2 text-5xl font-medium font-bold text-gray-900 sm:text-4xl title-font">News</h1>
        <div class="w-20 h-1 bg-indigo-500 rounded"></div>
      </div>
    </div>
  

     <!-- component -->
<!-- <div v-if="loading">Loading</div>
<div v-else> -->
  <div class="flex flex-wrap w-full">
    <div v-for="value in values" :key="value.title" class="p-2 xl:w-1/3 md:w-1/2">
    <div class="max-w-md py-4">
      <div class="relative transition duration-500 bg-white rounded-lg shadow-lg hover:shadow-xl">     
        <img class="object-cover w-full rounded-t-lg h-72 " :src="value.hdurl" alt="" />
        <div class="px-8 py-6 bg-white rounded-lg">
          <h1 class="mb-3 text-2xl font-bold text-gray-700 hover:text-gray-900 hover:cursor-pointer">{{ value.title }}</h1>
          <p class="tracking-wide text-gray-700">{{ value.explanation }}</p>
        </div>
        <div class="absolute px-4 py-2 bg-white rounded-lg top-2 right-2">
          <button class="text-md">$150</button>
        </div>
        </div>
      </div>
    </div>
  </div>
<!-- </div> -->
  </div>
</section>


   </div>
  </Layout>
</template>

<script>
import Layout from "./components/Layout.vue"
import Modal from './components/Modal.vue';

import axios from "axios"
const apikey = import.meta.env.VITE_NASA_API_KEY
const spinner = document.getElementById("spinner");
export default {
  components: {
    Layout,
    Modal
  },
  data() {
    return {
      isModalVisible: false,
      values: [],
      loading: false,
      }
  },
methods: {
  showModal() {
    this.isModalVisible = true;
  },
  closeModal(){
    this.isModalVisible = false;
  },

},
  mounted() {
    axios
    spinner.removeAttribute('hidden')
      .get(`https://api.nasa.gov/planetary/apod?api_key=${apikey}&start_date=2021-09-10`)
      .then(response => {
        this.values = response.data
       }) 
      
  },
}
</script>

<style>
.loader {
  border: 16px solid #f3f3f3;
  border-top: 16px solid #3498db;
  border-radius: 50%;
  width: 36px;
  height: 36px;
  animation: spin 2s linear infinite;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>