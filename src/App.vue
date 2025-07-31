<template>
  <div id="app" class="max-w-4xl w-full mx-auto bg-white rounded-lg shadow-xl overflow-hidden my-8">
    <!-- Componente de Cabeçalho da Cidade -->
    <HeaderCity :city-name="cityName" :description="cityDescription" />

    <!-- Componente de Filtro de Categoria -->
    <CategoryFilter
      :categories="uniqueCategories"
      :selected-category="currentCategory"
      @filter-category="updateCategory"
    />

    <!-- Componente de Lista de Pontos de Interesse -->
    <PointList :points="pointsOfInterest" :selected-category="currentCategory" />
  </div>
</template>

<script>
// Importa os componentes filhos que serão utilizados nesta aplicação.
import HeaderCity from './components/HeaderCity.vue';
import CategoryFilter from './components/CategoryFilter.vue';
import PointList from './components/PointList.vue';

export default {
  name: 'App', // Nome do componente raiz
  components: {
    // Registra os componentes filhos para que possam ser usados no template.
    HeaderCity,
    CategoryFilter,
    PointList
  },
  data() {
    return {
      cityName: 'Santiago do Chile',
      cityDescription: 'Santiago do Chile é a capital e maior cidade do Chile, localizada ao pé da imponente Cordilheira dos Andes. É um centro moderno e vibrante, que combina arquitetura histórica com construções contemporâneas, oferecendo uma rica cena cultural, gastronômica e de entretenimento. A cidade é conhecida por seus museus, parques, vinícolas próximas e vistas panorâmicas, como as do Cerro San Cristóbal. Além disso, Santiago é uma excelente base para explorar outras regiões do país, como as estações de esqui nos Andes ou as vinícolas do Vale do Maipo.',
      currentCategory: 'Todos', // Categoria inicialmente selecionada
      pointsOfInterest: [
        // História
        {
          name: 'Palacio de La Moneda',
          description: 'Sede do governo chileno, símbolo da história política do país. Possui visitas guiadas e a troca de guarda é uma atração à parte.',
          category: 'História',
          image: require('./assets/lamoneda.jpg'),
          link: 'https://pt.wikipedia.org/wiki/Palácio_de_La_Moneda'
        },
        {
          name: 'Plaza de Armas',
          description: 'Centro histórico da cidade, rodeada por prédios coloniais como a Catedral Metropolitana e o Museu Histórico Nacional.',
          category: 'História',
          image: 'lamoneda.jpg',
          link: 'https://pt.wikipedia.org/wiki/Mosteiro_dos_Jer%C3%B3nimos'
        },
        {
          name: 'Museu da Memória e dos Direitos Humanos',
          description: 'Espaço impactante dedicado às vítimas da ditadura de Pinochet. Visita fundamental para quem quer entender o Chile contemporâneo.',
          category: 'História',
          image: 'lamoneda.jpg',
          link: 'https://pt.wikipedia.org/wiki/Castelo_de_S%C3%A3o_Jorge'
        },
        {
          name: 'La Chascona',
          description: 'Uma das casas do poeta Pablo Neruda, localizada no bairro Bellavista. Repleta de elementos excêntricos, mistura arte, política e amor.',
          category: 'História',
          image: 'lamoneda.jpg',
          link: 'https://www.oceanario.pt/'
        },
        // Lazer
        {
          name: 'Cerro San Cristóbal',
          description: 'Um dos melhores mirantes da cidade. A subida pode ser feita a pé, de funicular ou teleférico. Lá em cima, há zoológico, trilhas e uma vista incrível.',
          category: 'Lazer',
          image: 'lamoneda.jpg',
          link: 'https://pt.wikipedia.org/wiki/Parque_das_Na%C3%A7%C3%B5es'
        },
        {
          name: 'Parque Bicentenario',
          description: 'Um parque moderno em Vitacura, com lagos artificiais, flamingos e ampla área verde. Ótimo para piqueniques e relaxar.',
          category: 'Lazer',
          image: 'lamoneda.jpg',
          link: 'https://pt.wikipedia.org/wiki/Bairro_Alto'
        },
        {
          name: 'Sky Costanera',
          description: 'O mirante mais alto da América Latina. Oferece uma vista panorâmica de 360º de Santiago e da Cordilheira dos Andes.',
          category: 'Lazer',
          image: 'lamoneda.jpg',
          link: 'https://pt.wikipedia.org/wiki/Alfama'
        },
        // Gastronomia
        {
          name: 'Elevador de Santa Justa',
          description: 'Um elevador neogótico que oferece vistas espetaculares da Baixa de Lisboa.',
          category: 'Gastronomia',
          image: 'lamoneda.jpg',
          link: 'https://pt.wikipedia.org/wiki/Elevador_de_Santa_Justa'
        },
          {
          name: 'Elevador de Santa Justa',
          description: 'Um elevador neogótico que oferece vistas espetaculares da Baixa de Lisboa.',
          category: 'Gastronomia',
          image: 'lamoneda.jpg',
          link: 'https://pt.wikipedia.org/wiki/Elevador_de_Santa_Justa'
        },
          {
          name: 'Elevador de Santa Justa',
          description: 'Um elevador neogótico que oferece vistas espetaculares da Baixa de Lisboa.',
          category: 'Gastronomia',
          image: 'lamoneda.jpg',
          link: 'https://pt.wikipedia.org/wiki/Elevador_de_Santa_Justa'
        },
        // Vida Noturna
        {
          name: 'Elevador de Santa Justa',
          description: 'Um elevador neogótico que oferece vistas espetaculares da Baixa de Lisboa.',
          category: 'Vida Noturna',
          image: 'lamoneda.jpg',
          link: 'https://pt.wikipedia.org/wiki/Elevador_de_Santa_Justa'
        },
          {
          name: 'Elevador de Santa Justa',
          description: 'Um elevador neogótico que oferece vistas espetaculares da Baixa de Lisboa.',
          category: 'Vida Noturna',
          image: 'lamoneda.jpg',
          link: 'https://pt.wikipedia.org/wiki/Elevador_de_Santa_Justa'
        },
          {
          name: 'Elevador de Santa Justa',
          description: 'Um elevador neogótico que oferece vistas espetaculares da Baixa de Lisboa.',
          category: 'Vida Noturna',
          image: 'lamoneda.jpg',
          link: 'https://pt.wikipedia.org/wiki/Elevador_de_Santa_Justa'
        },
        // Cultura
        {
          name: 'Elevador de Santa Justa',
          description: 'Um elevador neogótico que oferece vistas espetaculares da Baixa de Lisboa.',
          category: 'Cultura',
          image: 'lamoneda.jpg',
          link: 'https://pt.wikipedia.org/wiki/Elevador_de_Santa_Justa'
        },
          {
          name: 'Elevador de Santa Justa',
          description: 'Um elevador neogótico que oferece vistas espetaculares da Baixa de Lisboa.',
          category: 'Cultura',
          image: 'lamoneda.jpg',
          link: 'https://pt.wikipedia.org/wiki/Elevador_de_Santa_Justa'
        },
          {
          name: 'Elevador de Santa Justa',
          description: 'Um elevador neogótico que oferece vistas espetaculares da Baixa de Lisboa.',
          category: 'Cultura',
          image: 'lamoneda.jpg',
          link: 'https://pt.wikipedia.org/wiki/Elevador_de_Santa_Justa'
        },
        // Outras Atrações
        {
          name: 'Elevador de Santa Justa',
          description: 'Um elevador neogótico que oferece vistas espetaculares da Baixa de Lisboa.',
          category: 'Outras Atrações',
          image: 'lamoneda.jpg',
          link: 'https://pt.wikipedia.org/wiki/Elevador_de_Santa_Justa'
        },
          {
          name: 'Elevador de Santa Justa',
          description: 'Um elevador neogótico que oferece vistas espetaculares da Baixa de Lisboa.',
          category: 'Outras Atrações',
          image: 'lamoneda.jpg',
          link: 'https://pt.wikipedia.org/wiki/Elevador_de_Santa_Justa'
        },
          {
          name: 'Elevador de Santa Justa',
          description: 'Um elevador neogótico que oferece vistas espetaculares da Baixa de Lisboa.',
          category: 'Outras Atrações',
          image: 'lamoneda.jpg',
          link: 'https://pt.wikipedia.org/wiki/Elevador_de_Santa_Justa'
        },
      ]
    };
  },
  computed: {
    // Propriedade computada para extrair categorias únicas dos pontos de interesse.
    uniqueCategories() {
      const categories = new Set(this.pointsOfInterest.map(point => point.category));
      return ['Todos', ...Array.from(categories)];
    }
  },
  methods: {
    // Método para atualizar a categoria selecionada, acionado pelo CategoryFilter.
    updateCategory(category) {
      this.currentCategory = category;
    }
  }
};
</script>