<script setup>
const route = useRoute()
let id_perso = route.params.id
const User = await fetch("https://rickandmortyapi.com/api/character/" + route.params.id)
    .then((res) => res.json());
console.log(User)
</script >
<template>
    <div>
    <h1 class="text-3xl mb-4 font-mono font-bold">Edit personal info</h1>
        <section class="border-2 border-gray-300 rounded-lg p-10">
            <h1 class="text-2xl mb-10 font-mono font-semibold">Name : {{ User.name }}</h1>
            <h1 class="text-2xl mb-10 font-mono font-semibold">Status : {{ User.status }}</h1>
            <h1 class="text-2xl mb-10 font-mono font-semibold">Species : {{ User.species }}</h1>
            
        </section>
    </div>
</template>
<script>
    definePageMeta({
        layout: "custom",
    });
</script>

