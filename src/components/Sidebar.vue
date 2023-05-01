<template>
  <div class="sidebar">
    <h2>Selected Squares</h2>
    <ul>
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
}

ul {
  list-style: none;
  padding: 0;
}

li {
  margin-bottom: 8px;
}
</style>
