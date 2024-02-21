<template>
  <div class="container">
    <h1>Recipes</h1>
    <div class="pages">
      <button
        :disabled="pageNumber === 1 ? true : false"
        :class="pageNumber > 1 ? 'pageNum active' : 'pageNum'"
        @click="sliceRec(pageNumber - 1)"
      >
        &lt;
      </button>
      <button
        v-for="item in pageAmount"
        @click="sliceRec(item)"
        :class="pageNumber === item ? 'pageNum activePage' : 'pageNum'"
      >
        {{ item }}
      </button>
      <button
        :disabled="pageNumber === pageAmount ? true : false"
        :class="pageNumber < pageAmount ? 'pageNum active' : 'pageNum'"
        @click="sliceRec(pageNumber + 1)"
      >
        >
      </button>
    </div>
    <recipe-list :data="recipes"></recipe-list>
  </div>
</template>
<script setup>
import { onMounted, ref } from "vue";
import RecipeList from "./components/RecipeList.vue";

let result = ref([]);
let recipes = ref([]);
let elemOnPage = ref(0);
const pageAmount = ref(5);
let pageNumber = ref(1);

onMounted(async () => {
  await fetch("https://dummyjson.com/recipes")
    .then((res) => res.json())
    .then((data) => (result.value = data.recipes));
  elemOnPage.value = result.value.length / pageAmount.value;
  sliceRec(1);
});

function sliceRec(pageNum) {
  recipes.value = result.value.slice(
    (pageNum - 1) * elemOnPage.value,
    pageNum * elemOnPage.value
  );
  pageNumber.value = pageNum;
  console.log(recipes.value);
}
</script>
<style>
body {
  font-family: "Inter", sans-serif;
  display: flex;
  justify-content: center;
}
.container {
  width: 50vw;
}
h1 {
  font-weight: 400;
  font-size: 48px;
  text-align: center;
}
button {
  width: 64px;
  height: 64px;
  border: 1px solid #bdbdbd;
  color: #bdbdbd;
  background-color: transparent;
  font-weight: 800;
  font-size: 18px;
  border-radius: 6px;
}
p{
  font-weight: 700;
  font-size: 16px;
}
sup{
  font-weight: 400;
  font-size: 12px;
}
.active {
  color: #185bc3;
}
.activePage{
  background-color: #185bc3;
}
.pages {
  display: flex;
  justify-content: center;
}
.pageNum {
  margin: 0 10px 0 10px;
}
@media (width < 1420px) {
  .container{
    width: 80vw;
  }
}
</style>
