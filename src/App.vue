<template>
  <Test :numberList="numberList" v-on:buttonClicked="click"/>
  <MyInput :property="userName" @changed="changed"/>
  <MyInput :property="password" @changed="changed"/>
  <br/>
  <MyButton :background="red" :color="blue" :disabled="disabled" @buttonEvent="clicked"/>
  <pokemon :pokemon="pokemon"/>
  <Composition/>
  <div v-for="p in store.state.posts" :key="p.id">
    {{p.content}}
  </div>
</template>

#React Fragment is same as template in Vuejs

<script>
import Test from "./components/Test.vue"
import MyButton from "./components/MyButton.vue"
import MyInput from "./components/MyInput.vue"
import Pokemon from './components/Pokemon.vue'
import Composition from "./components/Composition.vue"
import {store} from "./components/microblog/index.js"
const api="https://pokeapi.co/api/v2/pokemon"
export default {
  name: "App",
  data() {
    return {
      numberList:[1,2,3,4,5,6],
      disabled:false,
      userName:{
        value:'',
        name:'userName'
        },
      password:{
        value:'',
        name:'password'
      },
      pokemon:null,
      pokemonIds:[1,4,7],
      store
    };
  },
  components:{
    Test,
    MyButton,
    MyInput,
    Pokemon,
    Composition
  },
  methods: {
    click(number){
      console.log('cliked',number)
      this.disabled=!this.disabled
    },
    clicked(){
      console.log(this.userName.value)
      console.log(this.password.value)
    },
    changed({name,value}){
      this[name].value=value
    },
    async fetchData(){
      const totalData=await Promise.all(this.pokemonIds.map((id)=>window.fetch(`${api}/${id}`)))
      const jsonData=await Promise.all(totalData.map((res)=>res.json()))
      this.pokemon=jsonData.map((data)=>{
        return {
        id:data.id,
        name:data.name,
        image:data.sprites.other['official-artwork'].front_default,
        types:data.types.map((type)=>type.type.name)
      }})
      console.log(this.pokemon)
    }
  },
  created(){
    this.fetchData()
  },
  mounted(){
    console.log('mounted')
  },
  updated(){
    console.log('updated')
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.underline {
  text-decoration: underline;
}
.danger {
  color: red;
  text-decoration: underline;
}
.success {
  color: green;
  text-decoration: underline;
}
.promoted {
  color: purple;
}
</style>
