<template>
    <div class="grow_animation">
        <NuxtLink :to="`${path}`">
        <svg fill="#000000" width="35px" height="35px" viewBox="0 0 1024 1024" xmlns="http://www.w3.org/2000/svg">
                <path d="M759.2 419.8L697.4 358 512 543.4 326.6 358l-61.8 61.8L512 667z"/>
            </svg>
        </NuxtLink>
    </div>
</template>
<script setup>
const {path} =defineProps(['path'])
</script>