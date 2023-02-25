<script setup>
onMounted(() => {
  if (!localStorage.getItem("token")) {
    // redirect to home page
    window.location.href = "/auth/login";
  }
});
definePageMeta({
  layout: "custom",
});
</script>

<template>
    <h1 class="text-3xl mb-4 font-mono font-bold">Managing contact</h1>
    <section class="border-2 border-gray-300 rounded-lg p-10">
        <h1 class="text-2xl mb-10 font-mono font-semibold">Contact information</h1>
        
    </section>
</template>
