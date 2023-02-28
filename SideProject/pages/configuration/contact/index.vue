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
         <FormKit
                type="form"
                @submit="submitApp"   
                :submit-attrs="{
                  inputClass: 'w-72 h-12 bg-blue-500 text-white font-bold text-xl rounded-full mt-4',
                
                }"    
            >
              <FormKit label="Title" 
                  :input-class="{
                  'border-2 border-gray-400 p-2 w-full rounded-xl font-mono mt-2': true,
                  }"
                  :messages-class="{
                  'text-red-500 p-4': true,
                  }"
                  :label-class="{
                      'text-xl font-mono':true
                  }"
                  :outer-class="{
                      'flex flex-col mt-4 mb-4': true,
                  }"
                  validation="required"
                  validation-visibility="dirty"
                  type="text" name="title" placeholder="Title..."
                />
              <FormKit label="Subtitle" 
                  :input-class="{
                  'border-2 border-gray-400 p-2 w-full rounded-xl font-mono mt-2': true,
                  }"
                  :messages-class="{
                  'text-red-500 p-4': true,
                  }"
                  :label-class="{
                      'text-xl font-mono':true
                  }"
                  :outer-class="{
                      'flex flex-col mt-4 mb-4': true,
                  }"
                  validation="required"
                  validation-visibility="dirty"
                  type="text" name="subtitle" placeholder="Subtitle..."
              />                
              <FormKit label="Description" 
                  :input-class="{
                  'border-2 border-gray-400 p-2 w-full rounded-xl font-mono mt-2': true,
                  }"
                  :messages-class="{
                  'text-red-500 p-4': true,
                  }"
                  :label-class="{
                      'text-xl font-mono':true
                  }"
                  :outer-class="{
                      'flex flex-col mt-4 mb-4': true,
                  }"
                  validation="required"
                  validation-visibility="dirty"
                  type="text" name="description" placeholder="Description..."
              />

              <FormKit label="Content"
                type="textarea"
                rows="10"
                cols="54"
                :input-class="{
                'border-2 rounded-3xl border-gray-400 text-xl font-thin mt-2 p-4': true,
                }"
                :messages-class="{
                'text-red-500 p-4': true,
                }"
                :label-class="{
                    'text-xl font-mono':true
                }"
                :outer-class="{
                    'flex flex-col mt-4 mb-4': true,
                }"
                validation="required"
                validation-visibility="dirty"
                name="content" placeholder="Content..."
              />
            </FormKit>
    </section>
</template>
