<template>
  <button
  :disabled="disabled"
  @click="clicked"
  >Click</button>
</template>

<script>
export default {
    name:'MyButton',
    props:{
        background:{
            type:String
        },
        color:{
            type:String
        },
        disabled:{
            type:Boolean
        }
    },
    methods:{
        clicked(){
            this.$emit("buttonEvent")
        }
    }
}
</script>

<style>

</style>