<template>
  <div class="character-card">
    <div class="card-image">
      <img :src="character.image" :alt="character.name" />
      <span :class="['status-badge', character.status.toLowerCase()]">
        {{ character.status }}
      </span>
    </div>

    <div class="card-content">
      <h3>{{ character.name }}</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CharacterCard',
  props: {
    character: {
      type: Object,
      required: true,
    },
  },
}
</script>

<style scoped>
.character-card {
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 14px;
  overflow: hidden;
  transition: all 0.3s ease;
  box-shadow: 0 0 15px rgba(56, 189, 248, 0.05);
  cursor: pointer;
}

.character-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 0 20px rgba(56, 189, 248, 0.25);
  border-color: #38bdf8;
}

.card-image {
  position: relative;
}

.card-image img {
  width: 100%;
  height: 260px;
  object-fit: cover;
  display: block;
  border-bottom: 1px solid #334155;
}

.status-badge {
  position: absolute;
  bottom: 12px;
  left: 12px;
  padding: 5px 12px;
  border-radius: 20px;
  font-size: 12px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  color: #fff;
}

.status-badge.alive {
  background-color: #22c55e;
  box-shadow: 0 0 10px rgba(34, 197, 94, 0.5);
}

.status-badge.dead {
  background-color: #ef4444;
  box-shadow: 0 0 10px rgba(239, 68, 68, 0.5);
}

.card-content {
  padding: 15px;
}

.card-content h3 {
  margin: 0;
  font-size: 1.1rem;
  font-weight: 600;
  color: #f8fafc;
  letter-spacing: 0.5px;
}
</style>
