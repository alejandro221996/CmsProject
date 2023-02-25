<script setup>
const route = useRoute()
// let id_perso = route.params.id
// const User = await fetch("https://rickandmortyapi.com/api/character/" + route.params.id)
//     .then((res) => res.json());
// console.log(User)
const User = {
    email: "pruena_test_123@gmail.com",
    first_name: "Prueba",
    last_name: "Test",
    username: "prueba_test_123"

}
</script >
<template>
    <div>
    <section class="border-2 border-gray-300 rounded-lg p-10">
            <h1 class="text-2xl mb-10 font-mono font-semibold">Edit information</h1>
            <FormKit
                type="form"
                v-if="!complete"
                id="editForm"
                @submit="submitEditHandler"
                :submit-attrs="{
                    inputClass: 'w-96 h-12 bg-blue-500 text-white font-bold text-xl rounded-full mt-4',
                
                }"
                submit-label="Save"
                
            >
                <FormKit label="Email" 
                        :input-class="{
                        'w-96 h-12  border-2 border-gray-400 rounded-full p-4 text-xl font-thin mt-2': true,
                        }"
                        :messages-class="{
                        'text-red-500': true,
                        }"
                        :label-class="{
                            'text-xl p-4 font-mono':true
                        }"
                         :value="`${User.email}`"
                        validation="required"
                        validation-visibility="dirty"
                        type="text" name="email" placeholder="Email..."
                />
                <FormKit label="Username" 
                        outer-class="mt-4"
                        :input-class="{
                        'w-96 h-12  border-2 border-gray-400 rounded-full p-4 text-xl font-thin mt-2': true,
                        }"
                        :messages-class="{
                        'text-red-500': true,
                        }"
                        :label-class="{
                            'text-xl p-4 font-mono':true
                        }"
                         :value="`${User.username}`"
                        validation="required"
                        validation-visibility="dirty"
                        type="text" name="username" placeholder="Username..."
                />
                <FormKit label="First Name" 
                        outer-class="mt-4"
                        :input-class="{
                        'w-96 h-12  border-2 border-gray-400 rounded-full p-4 text-xl font-thin mt-2': true,
                        }"
                        :messages-class="{
                        'text-red-500': true,
                        }"
                        :label-class="{
                            'text-xl p-4 font-mono':true
                        }"
                        :value="`${User.first_name}`"
                        validation="required"
                        validation-visibility="dirty"
                        
                        type="text" name="first_name" placeholder="First Name..."

                />
                <FormKit label="Last Name" 
                        outer-class="mt-4 mb-4"
                        :input-class="{
                        'w-96 h-12  border-2 border-gray-400 rounded-full p-4 text-xl font-thin mt-2': true,
                        }"
                        :messages-class="{
                        'text-red-500': true,
                        }"
                        :label-class="{
                            'text-xl p-4 font-mono':true
                        }"
                        :value="`${User.last_name}`"
                        validation="required"
                        validation-visibility="dirty"
                        type="text" name="last_name" placeholder="Last Name..."
                />
            </FormKit>
            <div v-else class="flex justify-center items-center">
                <div class="w-full h-24 flex justify-center items-center ">
                    <h1 class="text-3xl">Information was updated successfully 👍</h1>
                </div>
            </div>
        </section>
    </div>
</template>
<script>
    definePageMeta({
        layout: "custom",
    });
</script>

