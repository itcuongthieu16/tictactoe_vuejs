<template>
  <main class="pt-8 text-center">
    <h1 class="mb-8 text-5xl font-bold text-black">Tic Tac Toe</h1>

    <h3 class="text-xl mb-4 text-black font-bold">Lượt chơi: {{ player }}</h3>

    <Board :board="board" :makeMove="makeMove" />

    <div class="text-center">
      <h2 v-if="winner" class="text-6xl font-bold mb-8 text-black">Người chơi '{{ winner }}' đã chiến thắng!</h2>
      <ResetButton @click="resetGame" />
    </div>
  </main>
</template>

<script setup>
import { ref, computed } from 'vue'
import Board from './components/Board.vue'
import ResetButton from './components/ResetButton.vue'
import { toast } from 'vue3-toastify';
import 'vue3-toastify/dist/index.css';

const player = ref('X')
const board = ref(Array.from({ length: 3 }, () => Array.from({ length: 3 }, () => '')))

const CalculateWinner = (board) => {
  const lines = [[0, 1, 2], [3, 4, 5], [6, 7, 8], [0, 3, 6], [1, 4, 7], [2, 5, 8], [0, 4, 8], [2, 4, 6]]

  for (let i = 0; i < lines.length; i++) {
    const [a, b, c] = lines[i]

    if (board[a] && board[a] === board[b] && board[a] === board[c]) {
      return board[a]
    }
  }

  return null
}

const winner = computed(() => CalculateWinner(board.value.flat()))

const makeMove = (x, y) => {
  if (winner.value) return

  if (board.value[x][y]) return

  board.value[x][y] = player.value

  player.value = player.value === 'X' ? 'O' : 'X'
}

const resetGame = () => {
  toast.success("Reset Thành Công!")
  board.value = [
    ['', '', ''],
    ['', '', ''],
    ['', '', '']
  ]
  player.value = 'X'
}

</script>

<style>
body {
  @apply bg-[#3f7fbf] text-white;
}
</style>
