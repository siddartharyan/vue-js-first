<template>
  <div>
      <label :for="property.name">{{property.name}}</label>
  </div>
  <input :id="property.name" :value="property.value" @input="change"/>
</template>

<script>

export default {
    name:'MyInput',
    props:{
        property:{
            type:Object
        }
        
    },
    data(){
        return{
            value:''
        }
    },
    computed:{
    },
    methods:{
        change($event){
            this.$emit("changed",{
                name:$event.target.id,
                value:$event.target.value
            })
        }
    }
}
</script>

<style>

</style>