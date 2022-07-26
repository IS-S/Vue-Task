<template>
    <div>
        <form @submit.prevent="sortArr">
            <button type="submit">
                Sort
            </button>
        </form><form @submit.prevent="shuffleArr">
            <button type="submit">
                Shuffle
            </button>
        </form>
    </div>
</template>

<script>

    export default {
        methods: {
            shuffleArr() {
                this.$emit('shuffle-arr')
            },
            sortArr() {
                this.$emit('sort-arr')
            }
        }
    }
</script>

<style scoped>
</style>