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
        <h1 class="text-3xl">Add new media file</h1>
        <div class="flex flex-col mt-8">
            <label for="title">Title</label>
            <input type="text" name="title" id="title" class="border-2 border-gray-300 p-2">
        </div>
        <div class="flex flex-col">
            <label for="content">Descripcion</label>
            <textarea name="content" id="content" cols="30" rows="5" class="border-2 border-gray-300 p-2"></textarea>
        </div>
        <div class="flex flex-col">
            <label for="title">Title</label>
            <input type="file" name="file" id="file" class="border-2 border-gray-300 p-2">
        </div>
        <div class="flex flex-col mt-8">
            <button class="bg-blue-500 text-white p-2 rounded">Save</button>
        </div>  
    </div>
</template>
