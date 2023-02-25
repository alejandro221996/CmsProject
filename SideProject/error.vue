<template>
    <div class="flex justify-center items-center h-screen bg-slate-700">
        
    <div class="mt-7 max-w-sm mx-auto text-center border-2 rounded-3xl p-12">
        <p class="mt-7 text-7xl font-bold text-white">{{ error.statusCode }}</p>
        <p class="mt-7 text-3xl font-bold text-white">Oopss...</p>
        <p class="mt-7 text-3xl font-bold text-white">{{ error.message }}</p>
        
    </div>
</div>
</template>
<script setup>
    defineProps(['error']);
</script>