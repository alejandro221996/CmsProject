<style>
.formkit-actions .formkit-outer .formkit-wrapper button{
    background-color:blue;
    color:white;
    border-radius: 5px;
    border: none;
    padding: 10px 20px;
    font-size: 1.2rem;
    font-weight: 100;
    width: 100%;
}
</style>
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
        <h1 class="text-3xl">Add new post</h1>
        <FormKit
            type="form"
            #default="{ value }"
            @submit="submitApp"
            
        >
        <FormKit label="Title" 
            :input-class="{
            'border-2 border-gray-300 p-4 w-full rounded-xl font-mono': true,
            }"
            :messages-class="{
            'text-red-500 p-2': true,
            }"
            :label-class="{
                'text-xl p-4 font-mono':true
            }"
            :outer-class="{
                'mt-4 mb-4':true
            }"
            validation="required"
            validation-visibility="dirty"
            type="text" name="title" placeholder="Title..."
        />
        <FormKit
            type="textarea"
            label="Description"
            rows="10"
            cols="30"
            :input-class="{
                'border-2 border-gray-300 p-4 w-full rounded-xl font-mono': true,
            }"
            :messages-class="{
            'text-red-500 p-2': true,
            }"
            :label-class="{
                'text-xl p-4 font-mono':true
            }"
            validation="required"
            placeholder="Brief description about the post."
            name="description"
            />
        <FormKit
          type="file"
          label="Files"
          accept=".pdf,.doc,.docx,.xml,.md,.csv"
          multiple="true"
          :input-class="{
            ' border-2 w-96 border-gray-300 border-gray-400 rounded-xl p-4 ': true,
          }"
          :no-files-class="{
            'text-red-500 p-4': true,
          }"
          :outer-class="{
            'mb-4 mt-4': true,
          }"
          :messages-class="{
            'text-red-500 p-4': true,
          }"
          :label-class="{
            'text-xl p-4 font-mono':true
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
        <FormKit
            type="select"
            label="Status"
            name="status"
            :input-class="{
                'border-2 border-gray-300 p-4 rounded-xl w-full font-mono': true,
            }"
            :options="{
                published: 'Published',
                draft: 'Draft',
                
            }"
            :outer-class="{
                'mt-4 mb-4':true
            }"
            :label-class="{
                'text-xl p-4 font-mono':true
            }"
            validation="required"
        />
        </FormKit>
    </div>
</template>

