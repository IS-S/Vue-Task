<template>
    <div id="app">
        <h1>Array Play</h1>
        <hr />
        <SubmitNewConditions @newArray="newArray" />
        <ArrayManager @shuffle-arr="shuffleArr" @sort-arr="sortArr" />
        <hr />
        <div v-if="bsError">
            Array must be sorted before binsearch processing!
        </div>
        <div v-if="position != -1">
            Asked member of array is on {{position+1}} position.
        </div>
        <MainArray v-bind:array="array"
                   @look-for="lookFor" />
    </div>
</template>

<script>
    import SubmitNewConditions from '@/components/SubmitNewConditions';
    import ArrayManager from '@/components/ArrayManager'
    import MainArray from '@/components/MainArray'

    export default {
        name: 'app',
        data() {
            return {
                bsError: false,
                isSorted: false,
                position: -1,
                middle: -1,
                array: []
            }
        },
        components: {
            SubmitNewConditions,
            MainArray,
            ArrayManager
        },
        watch: {
            middle(value) {
                console.log("MIDDLE WATCH: " + value)
            }
        },
        methods: {
            newArray(arrParams) {
                this.array = new Array();
                console.log(typeof arrParams.maxVal + "/" + typeof arrParams.minVal + "/" + typeof arrParams.amtElm)
                for (let i = 0; i < arrParams.amtElm; i++) {
                    let rand = Math.floor((Math.random() * (arrParams.maxVal - arrParams.minVal + 1)) + arrParams.minVal);
                    console.log(rand);
                    this.array.push(rand)
                }
                this.isSorted = false;
                this.bsError = false;
                this.position = -1;
                
            },
            shuffleArr() {
                let trashArr = this.array;
                for (let i = trashArr.length - 1; i > 0; i--) {
                    let j = Math.floor(Math.random() * (i + 1)); // случайный индекс от 0 до i
                    [trashArr[i], trashArr[j]] = [trashArr[j], trashArr[i]];
                }
                this.array = new Array();
                for (let i = 0; i < trashArr.length; i++) {
                    this.array[i] = trashArr[i];
                }
                this.isSorted = false;
                this.bsError = false;
                this.position = -1;
            },
            sortArr() {
                this.array.sort(function (a, b) {
                    return a - b;
                });
                console.log(this.array)
                this.isSorted = true;
                this.bsError = false;
                this.position = -1;
            },
            lookFor(value) {
                if (this.isSorted === true) {
                    this.bsError = false;
                    let first = 0;    //left endpoint
                    let last = this.array.length - 1;   //right endpoint
                    let found = false;

                    while (found === false && first <= last) {
                        this.middle = Math.floor((first + last) / 2);
                        if (this.array[this.middle] == value) {
                            found = true;
                            this.position = this.middle;
                        } else if (this.array[this.middle] > value) {  //if in lower half
                            last = this.middle - 1;
                        } else {  //in in upper half
                            first = this.middle + 1;
                        }
                    }
                }
                else {
                    this.bsError = true;
                }
            }
        }
    };


</script>

<style>
</style>

