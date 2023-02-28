<script setup>
    onBeforeMount(() => {
        if (!localStorage.getItem("token")) {
            // redirect to home page
            window.location.href = "/auth/login";
        }
    });
    definePageMeta ({
        layout: 'custom',
    })
    const Users = await fetch("https://rickandmortyapi.com/api/character?page=1")
    .then((res) => res.json());
    const UserObj = Users.results
    //Count the number of users
    const count = UserObj.length;
</script >
<template>
    <h1 class="text-3xl mb-4 font-mono font-bold">Managing posts</h1>
        <section class="border-2 border-gray-300 rounded-lg p-10">
            <h1 class="text-2xl mb-10 font-mono font-semibold">Posts ({{ count }})</h1>
            <table class="w-full">
                <thead>
                    <tr class="border-b-2 border-gray-300 text-left text-xl font-mono font-semibold">
                        <th class="p-4">Username</th>
                        <th>Email</th>
                        <th>First Name</th>
                        <th>Last Name</th>
                        <th>Role</th>
                        <th class="text-center">Edit</th>
                        <th class="text-center">Delete</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="user in UserObj" :key="user.id" class="border-b-2 border-gray-300 font-mono text-xl font-mono font-thin">
                        <td class="p-4">{{user.id}}</td>
                        <td>{{user.status}}</td>
                        <td>{{user.gender}}</td>
                        <td>{{user.species}}</td>
                        <td>{{user.name}}</td>
                        <td class="">
                            <NuxtLink :to="`/users/${user.id}`" class="text-blue-500 flex justify-center items-center">
                                <IconsEditIcon/>
                            </NuxtLink>
                            <!-- Delete -->
                        </td>
                        <td class="">
                            <section class="flex justify-center items-center ">
                                <button class="" @click="deleteRec">
                                    <IconsDeleteIcon/>
                                </button>
                            </section>
                        </td>
                    </tr>
                </tbody>
            </table>
        </section>
</template>
