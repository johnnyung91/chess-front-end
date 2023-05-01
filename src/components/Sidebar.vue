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
  width: 200px;
  padding: 16px;
  background-color: #f5f5f5;
  position: absolute;
  top: 0;
  bottom: 0;
  right: 0;
}

.sidebar--mobile {
  position: relative;
  width: 100%;
  margin-top: 16px;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  margin-bottom: 8px;
}
</style>
