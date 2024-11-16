<script setup lang="ts">
const route=useRoute();

</script>

<template>
  
<NuxtLayout name = "navbar">
  <div>
    Page: index
    <h1>目前路由的路徑 - route.fullPath 為: {{ route.fullPath }}</h1>
  </div>
  </NuxtLayout>
</template>

<style scoped></style>
