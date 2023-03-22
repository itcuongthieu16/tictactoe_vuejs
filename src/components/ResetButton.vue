<template>
    <button @click="resetGame" class="px-4 py-2 bg-black rounded uppercase font-bold duration-300">
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