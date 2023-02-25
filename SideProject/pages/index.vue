<script setup>
onMounted(() => {
  if (!localStorage.getItem("token")) {
    // redirect to home page
    window.location.href = "/auth/login";
  }
});
const dataPage = {
  title: "Welcome to ",
  description: "Esta es mi pagina para citas.",
  subtitle: "This is a test page",
  image: "https://i.imgur.com/4Z5wQ9r.png",
  url: "https://www.google.com",
  company_name: "Phisyomel",
  company_url: "https://www.google.com",
  company_logo: "https://i.imgur.com/4Z5wQ9r.png",
}
const sectionHero = {
  title: "Im Jane Doe",
  subtitle: "And I'm a Photographer",
  buttonTxt:"Go to the gallery"
}
const postsSection = [
  {
    id:1,
    title: "Noteworthy technology acquisitions 2021",
    description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas molestie venenatis ipsum at vehicula.",
  },
  {
    id:2,
    title: "Noteworthy technology acquisitions 2022",
    description: "Here are the biggest enterprise technology acquisitions of 2021 so far, in reverse chronological order.",
  },
  {
    id:3,
    title: "Noteworthy technology acquisitions 2022",
    description: "Here are the biggest enterprise technology acquisitions of 2021 so far, in reverse chronological order.",
  },
  {
    id:4,
    title: "Noteworthy technology acquisitions 2022",
    description: "Here are the biggest enterprise technology acquisitions of 2021 so far, in reverse chronological order.",
  },
    {
    id:5,
    title: "Noteworthy technology acquisitions 2022",
    description: "Here are the biggest enterprise technology acquisitions of 2021 so far, in reverse chronological order.",
  },
  {
    id:6,
    title: "Noteworthy technology acquisitions 2022",
    description: "Here are the biggest enterprise technology acquisitions of 2021 so far, in reverse chronological order.",
  }
]
const qty_Posts= postsSection.length
</script>
<style>
.hero-image {
  background-image: url("../assets/images/backgroundImage.jpeg");
  background-color: #cccccc;
  height: 500px;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  position: relative;
}

.hero-text {
  text-align: center;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
}

</style>
<template>
  <div class="flex flex-col items-center justify-center min-h-screen py-2">
    <div class="flex flex-col items-center justify-center w-full flex-1 px-20 text-center">
      <h1 class="text-6xl font-bold mb-4">
        {{ dataPage.title }} {{ dataPage.company_name }}
      </h1>
      <p class="mt-3 text-2xl">
        {{ dataPage.description }}
      </p>
    </div>
    <div class="flex flex-col items-center justify-center w-full mt-6 mb-6 h-96 flex-1 px-20 text-center">
      <div class="w-full h-96 p-6 bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700 hero-image">
        <div class="hero-text">
          <h1 style="font-size:50px">{{ sectionHero.title }}</h1>
          <h3>{{ sectionHero.subtitle }}</h3>
          <button>{{ sectionHero.buttonTxt }}</button>
        </div>
      </div>
    </div>
    <div class="flex flex-col items-center justify-center w-full mt-6 mb-6 h-96 flex-1 px-20 text-center">
      <div :class="`grid grid-cols-3 rounded-xl bg-indigo-300 gap-4 w-42 p-6`">
          <div v-for="post in postsSection" :key="post.id">
              <a href="#" class="flex flex-col  items-center bg-white border border-gray-200 rounded-lg shadow md:flex-row md:max-w-xl hover:bg-gray-100 dark:border-gray-700 dark:bg-gray-800 dark:hover:bg-gray-700">
                <img class="object-cover w-full rounded-t-lg h-96 md:h-auto md:w-48 md:rounded-none md:rounded-l-lg" src="~/assets/images/login.png" alt="">
                <div class="flex flex-col justify-between p-4 leading-normal">
                    <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">{{ post.title }}</h5>
                    <p class="mb-3 font-normal text-gray-700 dark:text-gray-400">{{ post.description }}</p>
                </div>
              </a>           
          </div>
      </div>
     </div>
  </div>
</template>
