<template>
    <div>
        <ul>
            <ArrayItem
                v-for="item of array"
                v-bind:item="item"
                v-on:look-for="lookFor"
            />
        </ul>
    </div>
</template>

<script>

    import ArrayItem from '@/components/ArrayItem';

    export default {
        props: ['array'],
        components: {
            ArrayItem
        },
        methods: {
            lookFor(val) {
                this.$emit('look-for',val)
            }
        }
    }

</script>

<style scoped>
</style>