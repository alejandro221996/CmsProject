<script setup>

const User = {
  email: "pruena_test_123@gmail.com",
  first_name: "Prueba",
  last_name: "Test",
  username: "prueba_test_123",
  rol: "Admin",
  company: "Body Shop",

};
const asideOptions = [
  {
    name: 'Dashboard',
    link: '/configuration',
  },
  {
    name: 'Home',
    link: '/configuration/home',
  },
  {
    name: 'Info',
    link: '/configuration/info',
  },
  {
    name: 'Contact',
    link: '/configuration/contact',
  },
  {
    name: 'Posts',
    link: '/configuration/posts',
  },
  {
    name: 'Media',
    link: '/configuration/media',
  },
  {
    name: 'Pages',
    link: '/configuration/pages',
  },
  {

    name: 'Settings',
    link: '/configuration/settings'
  },
  {
    name: 'Users',
    link: '/configuration/users'
  }
];

</script>

<template>
<!-- container with one aside column and one main container -->
<div class="grid grid-cols-11  h-screen">
 <!-- Two columns  -->
    <!-- Aside column -->
    <aside class="bg-gray-100 col-span-2 border-2 border-gray-300">
      <!-- section with image -->
      <section class="h-full w-full ">
            <div class="w-full h-24 flex">
              <img class="w-20 h-20" src="~/assets/images/login.png" alt="logo" />
              <section class="flex flex-col justify-center pb-4">
                <p class="flex text-base items-center font-semibold text-gray-700 font-mono">{{ User.company }}</p>
                <p class="flex text-base items-center  font-semibold text-gray-500 font-mono">{{User.first_name}}({{ User.rol }})</p>
              </section>
              <picture class="flex justify-end items-center w-full pr-4">
                <IconsArrowIcon path="/"/>
              </picture>
            </div>
            <section class="h-auto w-full">
              <ul class="flex flex-col ">
                <li v-for="option in asideOptions" :key="option.name" class="flex p-6">
                    <article class="flex gap-6 justify-center ">
                      <!-- ICON -->
                      <div v-if="option.name==='Pages'">
                        <IconsPageIcon :path="`${option.link}`"/>
                      </div>
                      <div v-else-if="option.name==='Media'">
                        <IconsMediaIcon :path="`${option.link}`"/>
                      </div>
                      <div v-else-if="option.name==='Contact'">
                        <IconsContactIcon :path="`${option.link}`"/>
                      </div>
                      <div v-else-if="option.name==='Info'">
                        <NuxtLink class="hover:bg-sky-600 " :to="option.link">
                          <IconsInfoIcon :path="`${option.link}`"/>
                        </NuxtLink>
                      </div>
                      <div class="flex" v-else-if="option.name==='Posts'">
                        <IconsPostsIcon :path="`${option.link}`"/>
                      
                      </div>
                      <div v-else-if="option.name==='Home'">
                        <IconsHomeIcon :path="`${option.link}`"/>
                      </div>
                      <div v-else-if="option.name==='Users'">
                        <IconsUserIcon :path="`${option.link}`"/>
                        
                      </div>
                      <div v-else-if="option.name==='Dashboard'">
                        <IconsStadisticsIcon :path="`${option.link}`"/>
                      </div>
                      <div v-else>
                        <IconsSettingsIcon :path="`${option.link}`"/>
                      </div>
                      <p class=" flex items-center text-base font-semibold text-gray-700 font-mono">{{option.name}}</p>
                      <picture class="flex  items-center w-full pl-24" v-if="option.name==='Posts'||option.name==='Pages'||option.name==='Users'">
                          <IconsArrowIcon :path="`${option.link}`"/>
                      </picture>
                    </article>
                </li>
              </ul>
            </section>
      </section>
    </aside>
    <!-- Main column -->
    <main class="bg-white col-span-9">
      <section class="h-full w-full p-6 bg-white">
        <slot/>
      </section>
    </main>
</div>
</template>
