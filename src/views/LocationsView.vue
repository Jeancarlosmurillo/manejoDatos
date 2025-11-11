<template>
  <div class="locations-view">
    <h1>🌍 Locaciones</h1>

    <!-- Filtros -->
    <input v-model="searchTerm" placeholder="Buscar locación...">
    <select v-model="typeFilter">
      <option value="">Todos los tipos</option>
      <option value="Planet">Planeta</option>
      <option value="Space station">Estación espacial</option>
    </select>

    <!-- Grid de locaciones -->
    <div class="locations-grid">
      <LocationCard
        v-for="location in locations"
        :key="location.id"
        :location="location"
      />
    </div>
  </div>
</template>