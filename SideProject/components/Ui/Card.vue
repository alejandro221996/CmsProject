<script >

    export default {
    props: {
        title: String,
        quantity: String,
        percentage: String,
    },
}
</script>
<template>
    <div>
        <a href="#" class="block max-w-sm p-6 bg-white border-2 border-gray-200 rounded-lg shadow hover:bg-gray-100 dark:bg-gray-800 dark:border-gray-700 dark:hover:bg-gray-700">
            <div v-if="title==='Visitors'">
                <IconsPeopleIcon/>
            </div>
            <div v-else-if="title==='Users'">
                <IconsUsersIcon/>
            </div>
            <div v-else-if="title==='Likes'">
                <IconsLikeIcon/>
            </div>
            <div v-else-if="title==='Comments'">
                <IconsCommentsIcon/>
            </div>
            <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white font-mono">{{ title }}</h5>
            <span class="text-4xl font-medium text-gray-900 dark:text-white">{{ quantity }}</span><span class="ml-3 text-slate-400 text-md font-thin">{{quantity}}({{percentage}}%)</span>
        </a>
    </div>
</template>
