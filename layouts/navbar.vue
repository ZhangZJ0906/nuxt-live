<script setup></script>

<template>
    <nav class="navbar navbar-expand-lg bg-body-tertiary">
        <div class="container">
            <a class="navbar-brand" href="#">Navbar</a>
            <button class="navbar-toggler " type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
                aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon ">sss</span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav">
                    <li class="nav-item">
                        <NuxtLink class="nav-link active" to="/">首頁</NuxtLink>
                    </li>
                    <li class="nav-item">
                        <NuxtLink class="nav-link active"  to="/DayTwo">DayTwo</NuxtLink>
                    </li>
                    <li class="nav-item">
                        <NuxtLink class="nav-link active"  to="/D3">DayThree</NuxtLink>
                    </li>
                    <li class="nav-item">
                        <NuxtLink class="nav-link active"  to="/DayFour">DayFour</NuxtLink>
                    </li>
                    <li class="nav-item">
                        <NuxtLink class="nav-link active"  to="/DayFive">DayFive</NuxtLink>
                    </li>
                    <li class="nav-item">
                        <NuxtLink  class="nav-link active"  to="/D6/">DaySix</NuxtLink>
                    </li>
                    <li class="nav-item">
                        <NuxtLink  class="nav-link active"  to="/D7/">DaySeven</NuxtLink>
                    </li>
                    <li class="nav-item">
                        <NuxtLink  class="nav-link active"  to="/D8/">DayEight</NuxtLink>
                    </li>
                    <li class="nav-item">
                        <NuxtLink  class="nav-link active"  to="/D9/">DayNight</NuxtLink>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
    <main class="container">
        <slot />
    </main>
</template>

<style scoped></style>