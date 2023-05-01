<template>
  <div class="chessboard">
    <div v-for="(row, rowIndex) in rows" :key="row" class="row">
      <div
        v-for="(letter, letterIndex) in columns"
        :key="letter"
        :class="getCellClass(rowIndex, letterIndex, row, letter)"
        @click="handleCellClick(row, letter)"
      ></div>
    </div>
  </div>
</template>

<script setup>
import { ref, defineEmits, onMounted, onUnmounted } from "vue";
const columns = ["A", "B", "C", "D", "E", "F", "G", "H"];
const rows = [8, 7, 6, 5, 4, 3, 2, 1];

const emit = defineEmits(["cell-click"]);

const selectedCell = ref(null);

const getCellClass = (rowIndex, letterIndex, row, letter) => {
  const isBlack = (rowIndex + letterIndex) % 2 === 0;
  return {
    cell: true,
    black: isBlack,
    white: !isBlack,
    selected: selectedCell.value === `${letter}${row}`,
  };
};

const handleCellClick = (row, col) => {
  selectedCell.value = `${col}${row}`;
  emit("cell-click", selectedCell.value);
};

</script>

<style scoped>
.chessboard {
  display: flex;
  flex-wrap: wrap;
  width: 100%;
}

.row {
  display: flex;
  flex-direction: row;
  width: 100%;
}

.cell {
  flex: 1 0 12.5%;
  height: 0;
  padding-bottom: 12.5%;
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
