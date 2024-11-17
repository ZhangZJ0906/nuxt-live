<script setup>
definePageMeta({
    layout: 'day7'
})
const api_url = "https://nuxr3.zeabur.app/"
const roomsList = ref([]);

const getroom = () => {
    fetch(api_url + "api/v1/rooms/")
        .then((res) => res.json())
        .then((data) => {
            roomsList.value = data.result;
            // console.log(data);
        })
        .catch((error) => {
            console.error("API 调用失败：", error);
        });
}
onMounted(() => {
    getroom();
})


</script>

<template>
    <NuxtLayout></NuxtLayout>
    <h1>房型頁面</h1>
    <div class="container mt-4">
        <div class="row justify-content-center">
            <div class="col-8 col-md-6 col-lg-3" v-for="room in roomsList" :key="room.id">
                <div class="card h-100 shadow-sm" @click="getroom()">
                    <img :src="room.imageUrl" class="card-img-top" alt="Room Image" />
                    <div class="card-body d-flex flex-column">
                        <h3 class="card-title">{{ room.name }}</h3>
                        <p class="card-text flex-grow-1">{{ room.description }}</p>
                        <ul class="list-unstyled">
                            <li><strong>面積:</strong> {{ room.areaInfo }}</li>
                            <li><strong>床型:</strong> {{ room.bedInfo }}</li>
                            <li><strong>最大容納人數:</strong> {{ room.maxPeople }}</li>
                            <li><strong>價格:</strong> {{ room.price }}</li>
                            <NuxtLink to="/D7/_id">房型詳細頁面</NuxtLink>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.card-img-top {
    object-fit: cover;
    height: 200px;
    max-width: 100%;
}
</style>