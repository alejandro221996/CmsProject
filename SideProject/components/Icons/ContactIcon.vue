<template>
    <div class="grow_animation">
        <NuxtLink :to="`${path}`">
            <svg width="35px" height="35px" viewBox="0 0 14 14" role="img" focusable="false" aria-hidden="true" xmlns="http://www.w3.org/2000/svg">

                <path fill="#ff7043" d="M11.2 13H3.4V1h7.8c.66 0 1.2.54 1.2 1.2v9.6c0 .66-.54 1.2-1.2 1.2z"/>

                <path fill="#bf360c" d="M2.8 1h.6v12h-.6c-.66 0-1.2-.54-1.2-1.2V2.2c0-.66.54-1.2 1.2-1.2z"/>

                <g fill="#ab300b" transform="matrix(.3 0 0 .3 -.2 -.2)">

                <circle cx="26" cy="20" r="4"/>

                <path d="M33 30s-1.9-4-7-4-7 4-7 4v2h14v-2z"/>

                </g>

            </svg>
        </NuxtLink>
    </div>
</template>
<script setup>
const {path} =defineProps(['path'])

</script>
