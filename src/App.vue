<template>
  <Layout>
    <div >

<!-- component -->
<section class="text-gray-600 body-font">
  <div class="container px-5 py-24 mx-auto max-w-7x1">
    <div class="flex flex-wrap w-full p-4 mb-4">
      <div class="w-full mb-6 lg:mb-0">
        <h1 class="mb-2 text-5xl font-medium font-bold text-gray-900 sm:text-4xl title-font">News</h1>
        <div class="w-20 h-1 bg-indigo-500 rounded"></div>
      </div>
    </div>
    <div  class="flex flex-wrap -m-4">
      <div v-for="value in values" :key="value.title" class="p-4 xl:w-1/3 md:w-1/2">
        <div class="p-6 bg-white rounded-lg">
          <img class="object-cover object-center w-full mb-6 rounded lg:h-60 xl:h-56 md:h-64 sm:h-72 xs:h-72 h-72" :src="value.hdurl" alt="Image Size 720x400">
          <h3 class="text-xs font-medium tracking-widest text-indigo-500 title-font">SUBTITLE</h3>
          <h2 class="mb-4 text-lg font-medium text-gray-900 uppercase title-font">{{ value.title }}</h2>
          <p class="text-base leading-relaxed">{{ value.explanation }}.</p>
        </div>
      </div>
     
     
     
    </div>
  </div>
</section>


   </div>
  </Layout>
</template>

<script>
import Layout from "./components/Layout.vue"

import axios from "axios"
const apikey = import.meta.env.VITE_NASA_API_KEY

export default {
  components: {
    Layout,
  },
  data() {
    return {
      values: []
    }
  },

  mounted() {
    axios
      .get(`https://api.nasa.gov/planetary/apod?api_key=${apikey}&start_date=2021-09-10`)
      .then(response => {this.values = response.data})
  },
}
</script>
