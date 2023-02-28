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
    <h1 class="text-3xl mb-4 font-mono font-bold">Managing media files</h1>

    <section class="border-2 border-gray-300 rounded-lg p-10">
      <h1 class="text-2xl mb-10 font-mono font-semibold">Add new media file</h1>
      <FormKit
          type="form"
          v-if="!complete"
          id="registerForm"
          #default="{ value }"
          @submit="submitRecHandler"
          :submit-attrs="{
            inputClass: 'w-72 h-12 bg-blue-500 text-white font-bold text-xl rounded-full mt-4',
          
          }"           
        > 
      <FormKit
          type="file"
          label="Files"
          accept=".pdf,.doc,.docx,.xml,.md,.csv"
          multiple="true"
          :input-class="{
            ' border-2 w-2/5 border-gray-400 rounded-xl p-4 font-mono': true,
          }"
          :no-files-class="{
            'text-red-500 p-4 font-mono': true,
          }"
          :outer-class="{
            'mb-4 mt-4': true,
          }"
          :messages-class="{
            'text-red-500 p-4 font-mono': true,
          }"
          :label-class="{
            'text-xl font-mono':true
          }"
          :help-class="{
            'text-gray-500 p-4 font-mono': true,
          }"
          :file-name-class="{
            'text-gray-500 p-4 font-mono': true,
          }"
          :file-upload-button-class="{
            'text-gray-500 p-4 font-mono': true,
          }"
          :file-remove-class="{
            'text-red-500  font-mono': true,
          }"
          id="files"
      />
      <FormKit label="Description" 
          :input-class="{
          'h-12 w-2/5 border-2 border-gray-400 rounded-xl p-4 text-xl font-thin mt-2': true,
          }"
          :messages-class="{
          'text-red-500 p-4': true,
          }"
          :label-class="{
              'text-xl font-mono':true
          }"
          :outer-class="{
              'mb-4 mt-4': true,
          }"
          validation="required"
          validation-visibility="dirty"
          id="description"
          type="text" name="description" placeholder="Description..."
      />
      <FormKit label="Content"
          type="textarea"
          rows="10"
          cols="54"
          :input-class="{
          'border-2 rounded-xl border-gray-400 text-xl font-thin mt-2 p-4': true,
          }"
          :messages-class="{
          'text-red-500 p-4': true,
          }"
          :label-class="{
              'text-xl font-mono':true
          }"
          :outer-class="{
              'mb-4 mt-4': true,
          }"
          validation="required"
          validation-visibility="dirty"
          name="content" placeholder="Content..."
      />
      </FormKit>
    </section>
</template>
