<template>
  <div class="app">
    <div class="chessboard-container">
      <ChessBoard @cell-click="addSelectedCell" />
    </div>
    <div class="sidebar-container">
      <Sidebar :selectedCells="selectedCells" />
    </div>
  </div>
</template>

<script setup>
import ChessBoard from "./components/ChessBoard.vue";
import Sidebar from "./components/Sidebar.vue";

import { ref } from "vue";

const selectedCells = ref([]);

const addSelectedCell = (cell) => {
  selectedCells.value = [...selectedCells.value, cell];
};
</script>

<style scoped>
.app {
  display: flex;
  flex-direction: row;
}

.chessboard-container {
  position: relative;
  width: 60%;
}
.sidebar-container {
  position: relative;
  width: 40%;
}

@media only screen and (max-width: 600px) {
  .app {
    flex-direction: column;
  }

  .chessboard-container {
    width: 100%;
  }
  .sidebar-container {
    width: 100%;
  }
}
</style>
