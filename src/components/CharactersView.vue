<template>
  <div class="characters-view">
    <h1>Personajes Rick & Morty</h1>

    <!-- Barra de búsqueda -->
    <input
      v-model="filters.name"
      @input="handleSearch(filters.name)"
      type="text"
      placeholder="Buscar por nombre..."
      class="search-input"
    />

    <!-- Filtros -->
    <select v-model="filters.status" @change="applyFilter('status', filters.status)">
      <option value="">Todos los estados</option>
      <option value="alive">Vivo</option>
      <option value="dead">Muerto</option>
    </select>

    <!-- Loading -->
    <div v-if="loading" class="loading">
      <div class="spinner"></div>
      <p>Cargando personajes...</p>
    </div>

    <!-- Grid de personajes -->
    <div v-else class="characters-grid">
      <CharacterCard
        v-for="character in characters"
        :key="character.id"
        :character="character"
      />
    </div>
  </div>
</template>

<script>
import CharacterCard from './CharacterCard.vue'

export default {
  name: 'CharactersView',
  components: { CharacterCard },

  data() {
    return {
      filters: {
        name: '',
        status: '',
      },
    }
  },

  computed: {
    characters() {
      return this.$store.state.characters.characters
    },
    loading() {
      return this.$store.state.characters.loading
    },
    pagination() {
      return this.$store.state.characters.pagination
    },
  },

  methods: {
    loadCharacters() {
      this.$store.dispatch('characters/fetchCharacters')
    },
    handleSearch(term) {
      this.$store.dispatch('characters/setFilter', { key: 'name', value: term })
    },
    applyFilter(key, value) {
      this.$store.dispatch('characters/setFilter', { key, value })
    },
  },

  mounted() {
    this.loadCharacters()
  },
}
</script>

<style scoped>
.characters-view {
  max-width: 1200px;
  margin: 0 auto;
  text-align: center;
}

h1 {
  font-size: 2.3rem;
  color: #38bdf8;
  font-weight: 700;
  margin-bottom: 25px;
  text-shadow: 0 0 8px rgba(56, 189, 248, 0.5);
}

/* --- Búsqueda y filtros --- */
.search-input,
select {
  background: #1e293b;
  border: 1px solid #334155;
  color: #e2e8f0;
  border-radius: 10px;
  padding: 10px 14px;
  font-size: 14px;
  margin: 8px;
  transition: all 0.2s ease-in-out;
}

.search-input:focus,
select:focus {
  border-color: #38bdf8;
  outline: none;
  box-shadow: 0 0 8px rgba(56, 189, 248, 0.3);
}

/* --- Loading --- */
.loading {
  margin-top: 30px;
  color: #94a3b8;
  font-size: 1.1rem;
}

.spinner {
  width: 45px;
  height: 45px;
  border: 4px solid #334155;
  border-top: 4px solid #38bdf8;
  border-radius: 50%;
  margin: 0 auto 10px auto;
  animation: spin 0.9s linear infinite;
}

@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}

/* --- Grid --- */
.characters-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(230px, 1fr));
  gap: 25px;
  margin-top: 40px;
}
</style>
