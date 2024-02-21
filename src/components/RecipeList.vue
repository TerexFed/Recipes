<template>
  <div class="layout">
    <div v-for="(item, index) in data" :key="index" class="card">
      <recipe-item 
      :nameR="item.name"
      :image="item.image"
      :diff="item.difficulty"
      :cuisine="item.cuisine"
      :calPerSer="item.caloriesPerServing"
      :ingredients="item.ingredients"
      ></recipe-item>
    </div>
  </div>
</template>
<script setup>
import RecipeItem from './RecipeItem.vue';
defineProps({
  data: Array,
});
</script>
<style>
.layout {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  justify-items: center;
  grid-auto-rows: fit-content;
  margin-top: 50px;
  gap: 20px;
}
.card {
  box-sizing: border-box;
  border: 1px solid rgb(228, 228, 228);
  border-radius: 25px;
  box-shadow: 0px 4px 4px 0px rgba(0, 0, 0, 0.25);
  background: rgb(255, 255, 255);
}
img {
  height: 176.76px;
  width: 205px;
  border-radius: 25px 25px 0px 0px;
  background-position: center;
}
.name {
  width: 200px;
  padding-left: 5px;
}
.desc {
  display: flex;
  flex-direction: column;
  padding-left: 5px;
}
.ingredients {
  display: flex;
  flex-direction: column;
  padding-left: 5px;
  margin-top: 15px;
}
ul {
  display: flex;
  flex-direction: column;
  justify-content: left;
  margin-top: 5px;
  padding-inline-start: 20px;
}
li {
  font-weight: 400;
  font-size: 12px;
  width: 180px;
}
@media (width < 1420px) {
  .layout {
    grid-template-columns: repeat(2, 1fr);
  }
}
@media (width < 650px) {
  .layout {
    grid-template-columns: 1fr;
  }
}
</style>
