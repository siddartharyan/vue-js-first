<template>
<div v-for="(number,index) in numberList" :key="index">
    <button @click="handleClick(number)">Click Here {{number}}</button>
</div>
  
</template>

<script>
export default {
    name:'Test',
    data(){
        return{

        }
    },
    props:['numberList'],
    methods:{
        handleClick(number){
            this.$emit("buttonClicked",number)
        }
    }
}
</script>

<style>

</style>