<template>
  <div class="main-comp">
    <div id="card" v-for="(p, i) in pokemon" :key="i">
      <div id="title">{{ p.name }}</div>
      <div id="img">
        <img :src="p.image" />
      </div>
      <div id="description" v-for="t in p.types" :key="t">
        <div>{{ t }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Pokemon",
  props: ["pokemon"],
};
</script>

<style>
.main-comp{
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    width:50%;
}
#card{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    border:1px solid black;
    margin:2%
}
img{
    width:100%;
    height:60%
}
img:hover{
    background-color: bisque;
}
</style>
