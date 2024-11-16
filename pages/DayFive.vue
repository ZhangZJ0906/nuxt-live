<script setup>
import Loading from "vue-loading-overlay";
import "vue-loading-overlay/dist/css/index.css";
import { ref } from "vue";
const api_url = "https://nuxr3.zeabur.app/"
const newsList = ref([]);
const isLoading = ref(true);

// API 路徑 : https://nuxr3.zeabur.app/api/v1/home/news/
// 使用 ES6 fetch() 或是 axios.get() 串接 API
// 切換 isLoading 狀態

fetch(api_url + "api/v1/home/news/")
    .then((res) => res.json())
    .then((data) => {
        newsList.value = data.result;
        isLoading.value = false;
        console.log(data);
    })
    .catch((error) => {
        console.error("API 调用失败：", error);
        isLoading.value = false;
    });


</script>

<template>
    <h1><NuxtLink to="/">首頁</NuxtLink></h1>
    <h2>Page : DayFive</h2>
    <div class="container">
        <h1>最新消息</h1>
        <NewsCard v-for="item in newsList" :key="item._id" v-bind="item" />
        <ClientOnly>
            <Loading v-model:active="isLoading" />
        </ClientOnly>
    </div>
</template>

<style scoped>
.container {
    max-width: 1000px;
    margin: 0 auto;
}
</style>