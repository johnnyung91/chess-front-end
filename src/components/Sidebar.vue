<template>
  <div class="sidebar">
    <h2>Selected Squares</h2>
    <ul class="cells-grid">
      <li v-for="(cell, index) in selectedCells" :key="cell">
        {{ index + 1 }}: {{ cell }}
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref, computed, defineProps } from "vue";

const props = defineProps({
  selectedCells: {
    type: Array,
    default: () => [],
  },
});
</script>

<style scoped>
.sidebar {
  padding: 16px;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.cells-grid {
  list-style: none;
  padding: 0;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 0.5rem 1rem;
}

</style>
