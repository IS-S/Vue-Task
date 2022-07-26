<template>
    <div>
        <form @submit.prevent="onSubmit">
            Enter range of values
            <br>
            Minimum value:<input type="number" v-model.number="minVal"/>
            <br>
            Maxumum value:<input type="number" v-model.number="maxVal"/>
            <br>
            Enter amount of elements:<input type="number" v-model.number="amtElm" />
            <br>
            <button type="submit">
                Submit
            </button>
        </form>
    </div>

</template>

<script>
    export default {
        data() {
            return {
                minVal: Number,
                maxVal: Number,
                amtElm: Number
            }
        },
        methods:{
            onSubmit() {
                const arrParams = {
                    minVal : this.minVal,
                    maxVal : this.maxVal,
                    amtElm : this.amtElm
                }

                this.$emit('newArray', arrParams)
            }
        }
    }
</script>

<style scoped>
</style>