<style>
p{
  font-family: ;
}

</style>
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
                <p class="flex text-base items-center font-semibold text-gray-700 font-mono">Body Shop</p>
                <p class="flex text-base items-center  font-semibold text-gray-500 font-mono">Nicole(Admin)</p>
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
                        <IconsPageIcon/>
                      </div>
                      <div v-else-if="option.name==='Media'">
                        <IconsMediaIcon/>
                      </div>
                      <div v-else-if="option.name==='Contact'">
                        <IconsContactIcon/>
                      </div>
                      <div v-else-if="option.name==='Info'">
                        <NuxtLink class="hover:bg-sky-600 " :to="option.link">
                          <IconsInfoIcon/>
                        </NuxtLink>
                      </div>
                      <div class="flex" v-else-if="option.name==='Posts'">
                        <IconsPostsIcon/>
                      
                      </div>
                      <div v-else-if="option.name==='Home'">
                        <IconsHomeIcon/>
                      </div>
                      <div v-else-if="option.name==='Users'">
                        <IconsUserIcon/>
                      </div>
                      <div v-else>
                        <IconsSettingsIcon/>
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
<script >
import {ref} from 'vue'

export default {
  name:"custom",
  setup() {
    const menuPosts = ref(false);
    const togglePostsMenu = () => {
      menuPosts.value = !menuPosts.value;
    };
    const menuPages = ref(false);
    const togglePagesMenu = () => {
      console.log("togglePagesMenu")
      menuPages.value = !menuPages.value;
    };
    return {
      menuPosts,
      togglePostsMenu,
      menuPages,
      togglePagesMenu
    };
  },
  computed: {
    multiple_value_boolean() { 
      return "Posts" || "Pages"
    } 
  },
  data() {
    const asideOptions=[
      {
        name: 'Home',
        link: '/home',
      },
      {
        name: 'Info',
        link: '/info',
      },
      {
        name: 'Contact',
        link: '/contact',
      },
      {
        name: 'Posts',
        link: '/posts',
      },
      {
        name: 'Media',
        link: '/media',
      },
      {
        name: 'Pages',
        link: '/pages',
      },
      {

        name: 'Settings',
        link: '/settings'
      },
      {
        name: 'Users',
        link: '/users'
      }
    ]
    return {
      asideOptions,
    };
  }
}

</script>
