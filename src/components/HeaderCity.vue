<template>
  <div class="header-city p-8 bg-gradient-to-r from-purple-600 to-purple-800 text-white text-center rounded-t-lg">
    <h1 class="text-4xl font-extrabold mb-2">{{ cityName }}</h1>
    <p class="text-xl font-light opacity-90">{{ description }}</p>
  </div>
</template>

<script>
export default {
  name: 'HeaderCity', // Nome do componente
  props: {
    cityName: String, // Propriedade para o nome da cidade
    description: String // Propriedade para a descrição da cidade
  }
};
</script>