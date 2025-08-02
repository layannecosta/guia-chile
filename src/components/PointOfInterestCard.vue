<template>
  <div class="point-card bg-white rounded-lg shadow-md overflow-hidden transform transition duration-300 hover:scale-105">
   <img :src="imageUrl" :alt="point.name" class="w-full h-48 object-cover">
    <div class="p-5">
      <h3 class="text-xl font-bold text-gray-900 mb-2">{{ point.name }}</h3>
      <p class="text-gray-700 text-sm mb-3">{{ point.description }}</p>
      <div class="flex items-center text-gray-600 text-sm">
        <i class="fas fa-tag mr-2 text-purple-500"></i>
        <span>{{ point.category }}</span>
      </div>
      <a :href="point.link" target="_blank" rel="noopener noreferrer"
         class="mt-4 inline-block bg-purple-500 text-white px-4 py-2 rounded-full text-sm font-medium
                hover:bg-purple-600 transition duration-300">
        Ver Mais <i class="fas fa-external-link-alt ml-2"></i>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PointOfInterestCard',
  props: {
    point: Object
  }
}
</script>
