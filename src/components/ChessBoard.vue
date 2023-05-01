<template>
  <div class="chessboard">
    <div v-for="row in 8" :key="row" class="row">
      <div
        v-for="col in 8"
        :key="col"
        :class="getCellClass(row, col)"
        @click="handleCellClick(row, col)"
      ></div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const selectedCell = ref(null);

const getCellClass = (row, col) => {
  const isBlack = (row + col) % 2 === 0;
  return {
    cell: true,
    black: isBlack,
    white: !isBlack,
    selected: selectedCell.value === `${row}${col}`,
  };
};

const handleCellClick = (row, col) => {
  selectedCell.value = `${row}${col}`;
};
</script>

<style scoped>
.chessboard {
  display: flex;
  flex-direction: column;
  width: 320px;
  height: 320px;
}

.row {
  display: flex;
  flex-direction: row;
  width: 100%;
}

.cell {
  width: 40px;
  height: 40px;
  border: 1px solid black;
}

.black {
  background-color: #769656;
}

.white {
  background-color: #eeeed2;
}

.selected {
  background-color: #69c2ff;
}
</style>
