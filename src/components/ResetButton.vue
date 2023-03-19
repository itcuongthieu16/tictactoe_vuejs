<template>
    <button @click="resetGame" class="px-4 py-2 bg-pink-500 rounded uppercase font-bold hover:bg-pink-600 duration-300">
        Chơi lại
    </button>
</template>

<script>
export default {
    props: {
        resetGame: {
            type: Function,
            required: true
        }
    }
}
</script>