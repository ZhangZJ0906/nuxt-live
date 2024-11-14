<script setup lang="ts">
const route=useRoute();

</script>

<template>
  <NuxtLink to="/DayTwo">DayTwo</NuxtLink>
  <br>
  <NuxtLink to="/D3">DayThree</NuxtLink>
  <br>
  <NuxtLink to="/DayFour">DayFour</NuxtLink>
  <div>
    Page: index
    <h1>目前路由的路徑 - route.fullPath 為: {{ route.fullPath }}</h1>
  </div>
</template>

<style scoped></style>
