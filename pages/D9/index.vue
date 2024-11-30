<script setup>
const routre = useRoute();
navigateTo("/D9/register");
</script>

<template>
    <div>Page: index</div>
    <button type="button" class="btn btn-primary" @click="routre.push('/')"></button>
</template>

<style scoped></style>