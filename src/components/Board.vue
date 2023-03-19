<template>
    <div class="flex flex-col items-center mb-8">
        <div v-for="(row, x) in board" :key="x" class="flex">
            <div v-for="(cell, y) in row" :key="y" :class="[
                'border',
                'border-white',
                'w-24',
                'h-24',
                'hover:bg-gray-700',
                'flex',
                'items-center',
                'justify-center',
                'material-icons-outlined',
                'text-4xl',
                'cursor-pointer',
                cell === 'X' ? 'text-pink-500' : 'text-blue-400',
            ]" @click="makeMove(x, y)">
                {{ cell === 'X' ? 'X' : cell === 'O' ? 'O' : '' }}
            </div>
        </div>
    </div>
</template>
<script>
export default {
    props: {
        board: {
            type: Array,
            required: true,
        },
        makeMove: {
            type: Function,
            required: true,
        },
    },
};
</script>