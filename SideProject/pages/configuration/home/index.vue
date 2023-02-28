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
   <h1 class="text-3xl mb-4 font-mono font-bold">Managing home page</h1>
    <section class="border-2 border-gray-300 rounded-lg p-10">
        <h1 class="text-2xl font-mono font-bold">Add new home configuration</h1>
        <FormKit
            type="form"
            #default="{ value }"
            @submit="submitApp"
            :submit-attrs="{
                inputClass: 'w-full p-4 bg-blue-500 text-white font-bold font-mono text-xl rounded-full mt-4',
            
            }"
            
        >
        <div class="mt-8 border-2 border-gray-300 rounded-lg p-10">
            <h2 class="text-2xl font-bold">First section</h2>
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
                type="text" name="title_first" placeholder="Title..."
            />
            <FormKit label="Subtitle" 
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
                type="text" name="subtitle" placeholder="Subtitle..."
            />
        </div>
        <div class="mt-8 border-2 border-gray-300 rounded-lg p-10">
            <h2 class="text-2xl font-bold">Second section</h2>
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
                type="text" name="title_second" placeholder="Title..."
            />
            <FormKit label="Description" 
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
                type="text" name="description_second" placeholder="Description..."
            />
            <FormKit
                type="file"
                label="Image"
                accept=".jpeg,.jpg,.png"
                multiple="true"
                :input-class="{
                    ' border-2 w-2/5 border-gray-300 rounded-xl p-4 font-mono': true,
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
                id="image"
            />
        </div>
        </FormKit>
    </section>
</template>
