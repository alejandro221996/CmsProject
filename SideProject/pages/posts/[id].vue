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
  <div>
    <h1>Post1</h1>
  </div>
</template>

<style lang="scss" scoped>

</style>