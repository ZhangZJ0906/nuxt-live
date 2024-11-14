<script setup lang="ts"></script>

<template>

  <header>
    <ul class="list">
      <li>
        <NuxtLink to="/">首頁</NuxtLink>
      </li>
      <li>
        <NuxtLink to="/D3/">前台首頁</NuxtLink>
      </li>
      <li>
        <NuxtLink to="/D3/about">前台 About</NuxtLink>
      </li>
      <li>
        <NuxtLink to="/D3/admin">前往 後台首頁</NuxtLink>
      </li>
      <li>
        <NuxtLink to="/D3/admin/order">前往 後台訂單</NuxtLink>
      </li>
    </ul>
  </header>
  <slot />
  <footer>
    <h5>
      前台模板的表尾
    </h5>
  </footer>

</template>

<style scoped lang="scss"></style>
