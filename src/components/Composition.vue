<template>
  <button @click="increment">{{count}}</button>
  <button @click="incrementN('a')">{{numbers.a}}</button>
  <button @click="incrementN('b')">{{numbers.b}}</button>
  <p>{{total}}</p>
</template>

<script>
import {computed, reactive, ref, watch} from 'vue'
export default {
    name:"Composition",
    setup(){
        const count=ref(0)
        const numbers=reactive({
            'a':0,
            'b':0
        })
        function increment(){
            count.value++
        }
        function incrementN(n){
            numbers[n]++
        }
        const total=computed(()=>count.value+numbers.a+numbers.b)
        watch(numbers,(newVal)=>{
            console.log(newVal)
        })
        return{
            count,
            increment,
            numbers,
            incrementN,
            total
        }
    }
}
</script>

<style>

</style>