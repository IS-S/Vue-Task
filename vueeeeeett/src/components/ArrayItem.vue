<template>
        <button v-on:click="$emit('look-for',item)">
            {{item}}
        </button>
</template>

<script>
    export default {
        props: ['item'] 
    }
</script>

<style scoped>
    button {
        background: #008EB0; /* Синий цвет фона */
        color: #fff; /* Белый цвет текста */
        margin-bottom: 1rem; /* Отступ снизу */
    }
    .green {
        background: #73A353;
    }
    .red {
        background: #C1172C;
    }
    .orange {
        background: #F7941E;
    }
</style>