<template>
  <img :src="image" alt="foodpic" />
  <p class="name">{{ nameR }}</p>
  <div class="desc">
    <sup>Difficulty: {{ diff }}</sup>
    <sup>Cuisine: {{ cuisine }}</sup>
    <sup>Calories per Serving: {{ calPerSer }}</sup>
  </div>
  <div class="ingredients">
    <sup><b>Ingredients:</b></sup>
    <ul>
      <li v-for="(ingr, ind) in ingredients" :key="ind">{{ ingr }}</li>
    </ul>
  </div>
</template>
<script setup>
defineProps({
  nameR: String,
  image: String,
  diff: String,
  cuisine: String,
  calPerSer: Number,
  ingredients: Array
});
</script>
<style>
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

</style>
