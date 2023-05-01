<template>
  <div class="app">
    <div class="chessboard-container">
      <ChessBoard @cell-click="addSelectedCell" />
    </div>
    <Sidebar :selectedCells="selectedCells" />
  </div>
</template>

<script setup>
import ChessBoard from "./components/ChessBoard.vue";
import Sidebar from "./components/Sidebar.vue";

import { ref } from "vue";

const selectedCells = ref([]);

const addSelectedCell = (cell) => {
  selectedCells.value = [...selectedCells.value, cell];
  console.log(selectedCells.value);
};
</script>

<style scoped>
.app {
  display: flex;
  flex-direction: row;
}

.chessboard-container {
  position: relative;
  margin-right: 16px;
}
</style>
