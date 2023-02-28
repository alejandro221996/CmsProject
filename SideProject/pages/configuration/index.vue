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

</script >
<template>
    <div>
        <h1 class="text-3xl mb-4 font-mono font-bold">Dashboard</h1>
        <section class="border-2 border-gray-300 rounded-lg p-10">
            <h2 class="text-2xl mb-4 font-mono font-bold">Statistics</h2>
            <div class='grid md:grid-cols-3 sm:grid-cols-1 rounded-xl bg-teal-50 gap-4 w-42 p-6'>
                <!-- Passing the component IconsPeopleIcon through UiCard component -->
                <UiCard title="Visitors" quantity="3" percentage="50" />
                <!-- Passing the component IconsUsersIcon through UiCard component -->
                <UiCard title="Users" quantity="15" percentage="20" />
                <!-- Passing the component IconsLikeIcon through UiCard component -->
                <UiCard title="Likes" quantity="30" percentage="60" />
                <!-- Passing the component InfoIcon through UiCard component -->
                <UiCard title="Comments" quantity="0" percentage="0" />
            </div>
        </section>
    </div>
</template>
