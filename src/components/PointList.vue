<template>
  <div class="point-list p-8 bg-white">
    <h2 class="text-2xl font-semibold text-gray-800 mb-6 border-b-2 border-purple-400 pb-2">Pontos de Interesse</h2>
    <div v-if="filteredPoints.length === 0" class="text-center text-gray-600 text-lg py-10">
      Nenhum ponto de interesse encontrado para esta categoria.
    </div>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      <PointOfInterestCard v-for="point in filteredPoints" :key="point.name" :point="point" />
    </div>
  </div>
</template>

<script>
import PointOfInterestCard from './PointOfInterestCard.vue'; // Importa o componente do cartão de ponto de interesse

export default {
  name: 'PointList', // Nome do componente
  components: {
    PointOfInterestCard // Registra o componente filho
  },
  props: {
    points: Array, // Propriedade para a lista completa de pontos de interesse
    selectedCategory: String // Propriedade para a categoria selecionada para filtragem
  },
  computed: {
    // Propriedade computada para filtrar os pontos com base na categoria selecionada.
    filteredPoints() {
      if (this.selectedCategory === 'Todos') {
        return this.points; // Retorna todos os pontos se a categoria for 'Todos'
      }
      // Filtra os pontos que correspondem à categoria selecionada
      return this.points.filter(point => point.category === this.selectedCategory);
    }
  }
};
</script>
