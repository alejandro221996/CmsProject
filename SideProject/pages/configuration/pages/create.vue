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
        <h1 class="text-2xl font-mono font-semibold">Add new page</h1>
        <section class="border-2 border-gray-300 rounded-lg p-10 mt-5">
            <h1 class="text-2xl  font-mono font-semibold">Page information</h1>
            <FormKit
                type="form"
                @submit="submitApp"      
            >
                <div class="flex flex-col mt-4 mb-4">
                <FormKit label="Title" 
                        :input-class="{
                        'border-2 border-gray-400 p-2 w-full rounded-xl font-mono mt-2': true,
                        }"
                        :messages-class="{
                        'text-red-500': true,
                        }"
                        :label-class="{
                            'text-xl font-mono ':true
                        }"
                        validation="required"
                        validation-visibility="dirty"
                        type="text" name="title" placeholder="Title 1..."
                    />
                </div>
                <div class="flex flex-col mt-4 mb-4">
                    <FormKit
                        type="textarea"
                        label="Content"
                        rows="10"
                        cols="30"
                        :input-class="{
                            'border-2 border-gray-400 p-2 w-full rounded-xl font-mono mt-2': true,
                        }"
                        :messages-class="{
                        'text-red-500 ': true,
                        }"
                        :label-class="{
                            'text-xl font-mono':true
                        }"
                        validation="required"
                        placeholder="Remember to write in complete sentences."
                        name="content"
                        />
                </div>
                <div class="flex flex-col mb-4">
                    <FormKit
                        type="select"
                        label="Status"
                        name="status"
                        :input-class="{
                            'border-2 border-gray-400 p-2 w-full rounded-xl font-mono mt-2': true,
                        }"
                        :messages-class="{
                            'text-red-500': true,
                        }"
                        :label-class="{
                            'text-xl font-mono ':true
                        }"
                        :options="{
                            published: 'Published',
                            draft: 'Draft',
                            
                        }"
                        validation="required"
                    />
                </div>
            </FormKit>
        </section>
    </div>
</template>

