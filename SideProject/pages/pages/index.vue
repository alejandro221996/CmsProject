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
    <div class="mt-8">
        <h1 class="text-3xl">Pages</h1>   
    </div>
</template>
