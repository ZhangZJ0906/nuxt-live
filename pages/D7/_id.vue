<script setup lang="ts">
import { useRouter } from 'vue-router'
const router = useRouter()
function geback() {
    router.push('/D7')
}


</script>
<template>
    <h2>房型詳細頁面</h2>
    <button class="btn btn-primary" type="button" @click="geback">go back</button>
</template>