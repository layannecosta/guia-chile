<template>
  <div class="category-filter p-6 bg-gray-100 border-b border-gray-200">
    <h3 class="text-xl font-semibold text-gray-800 mb-4">Filtrar por Categoria:</h3>
    <div class="flex flex-wrap gap-3 justify-center">
      <button
        v-for="category in categories"
        :key="category"
        @click="$emit('filter-category', category)"
        :class="{'bg-purple-600 text-white shadow-md': selectedCategory === category, 'bg-gray-200 text-gray-700 hover:bg-gray-300': selectedCategory !== category}"
        class="px-5 py-2 rounded-full font-medium transition duration-300 ease-in-out transform hover:scale-105"
      >
        {{ category }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CategoryFilter', // Nome do componente
  props: {
    categories: Array, // Propriedade para a lista de categorias disponíveis
    selectedCategory: String // Propriedade para a categoria atualmente selecionada
  },
  emits: ['filter-category'] // Declara o evento 'filter-category' que este componente pode emitir
};
</script>
