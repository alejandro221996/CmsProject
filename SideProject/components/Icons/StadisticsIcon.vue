<template>
    <div class="grow_animation">
        <NuxtLink :to="`${path}`">
            <svg fill="#000000" width="35px" height="35px" viewBox="0 0 24 24" id="dashboard-alt" data-name="Flat Line" xmlns="http://www.w3.org/2000/svg" class="icon flat-line">
                <g id="SVGRepo_bgCarrier" stroke-width="0"></g>
                <g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g>
                <g id="SVGRepo_iconCarrier"><path id="secondary" d="M3,9H21a0,0,0,0,1,0,0V20a1,1,0,0,1-1,1H4a1,1,0,0,1-1-1V9A0,0,0,0,1,3,9Z" style="fill: #2ca9bc; stroke-width: 2;"></path>
                <path id="primary" d="M3,9H21M15,9V20m6,0V4a1,1,0,0,0-1-1H4A1,1,0,0,0,3,4V20a1,1,0,0,0,1,1H20A1,1,0,0,0,21,20Z" style="fill: none; stroke: #000000; stroke-linecap: round; stroke-linejoin: round; stroke-width: 2;"></path>
                </g>
            </svg>
        </NuxtLink>
    </div>
    
</template>
<script setup>
const {path} =defineProps(['path'])

</script>
