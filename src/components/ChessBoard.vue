<template>
  <div class="chessboard">
    <div v-for="row in 8" :key="row" class="row">
      <div v-for="col in 8" :key="col" :class="getCellClass(row, col)"></div>
    </div>
  </div>
</template>

<script setup>
const getCellClass = (row, col) => {
  const isBlack = (row + col) % 2 === 0;
  return {
    cell: true,
    black: isBlack,
    white: !isBlack,
  };
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
}

.black {
  background-color: #769656;
}

.white {
  background-color: #eeeed2;
}
</style>
