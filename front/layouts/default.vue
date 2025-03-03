<template>
    <header class="flex flex-row items-center w-full bg-gray-900 border-b-2 border-cyan-400 text-white p-4 shadow-lg max-sm:justify-between max-sm:relative relative ">
        <div class="basis-1/4 flex items-center justify-start px-8 min-w-40 max-sm:basis-auto">
            <img src="assets/images/tlogo.jpeg" class="w-16 h-16 rounded-full bg-transparent">
        </div>
        <div class="basis-1/4 max-sm:basis-auto">
        </div>
        <nav :class ="{'basis-1/2 flex flex-row items-center justify-end px-8 gap-4': !burger || burger,
        'max-sm:basis-auto max-sm:absolute max-sm:top-full max-sm:w-full max-sm:justify-center max-sm:flex-col max-sm:gap-0 max-sm:bg-white max-sm:px-0':burger,
        'max-sm:hidden': !burger}">
            <NuxtLink to="/" class="my-auto p-2 hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:border-b-2 max-sm:border-black max-sm:text-black max-sm:text-center px-4 py-2 rounded-lg transition-all duration-300 hover:bg-gray-700">Home</NuxtLink>
            <div class = "my-auto p-2 hover:bg-gray-500 hover:text-white max-sm:text-black max-sm:w-full max-sm:px-0 max-sm:pb-0 max-sm:flex max-sm:text-center max-sm:flex-col">
              <div @click="switch_submenu" class="cursor-pointer border-b-2 border-cyan-400 max-sm:border-black p-1">Labs</div>
              <div v-show="submenu" class= "flex flex-col absolute top-full bg-white text-black w-56 text-center max-sm:relative max-sm:w-full max-sm:bg-sky-300">
                <NuxtLink to = "/login" class = "my-auto p-2 border-b-2 border-black hover:bg-gray-500 text-black hover:text-white max-sm:w-full max-sm:border-t-2 max-sm:text-center">Lab3</NuxtLink>
                <NuxtLink to = "/login" class = "my-auto p-2 border-b-2 border-black hover:bg-gray-500 text-black hover:text-white max-sm:w-full max-sm:text-center">Lab4</NuxtLink>
                <NuxtLink to = "/login" class = "my-auto p-2 border-b-2 border-black hover:bg-gray-500 text-black hover:text-white max-sm:w-full max-sm:text-center">Lab5</NuxtLink>
                <NuxtLink to = "/login" class = "my-auto p-2 border-b-2 border-black hover:bg-gray-500 text-black hover:text-white max-sm:w-full max-sm:border-black max-sm:text-center">Lab6</NuxtLink>
              </div>
            </div>
            <NuxtLink to="/login" class="my-auto p-2 hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:border-b-2 max-sm:border-black max-sm:text-center px-4 py-2 rounded-lg transition-all duration-300 hover:bg-gray-700 max-sm:text-black">LogIn</NuxtLink>
            <NuxtLink to="/logout" class="my-auto p-2 hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:border-b-2 max-sm:border-black max-sm:text-center px-4 py-2 rounded-lg transition-all duration-300 hover:bg-gray-700 max-sm:text-black">LogOut</NuxtLink>
        </nav>
        <div v-if = "!burger" @click = "switch_burger" class = "max-sm:flex max-sm:flex-col max-sm:mr-8 max-sm:justify-between max-sm:items-center max-sm:w-8 max-sm:h-6">
          <span class = "h-[3px] w-full bg-white"></span>
          <span class = "h-[3px] w-full bg-white"></span>
          <span class = "h-[3px] w-full bg-white"></span>
        </div>
        <div v-else  class = "max-sm:flex max-sm:flex-col max-sm:mr-8 max-sm:justify-between max-sm:items-center max-sm:w-8 max-sm:h-6" @click = "switch_burger">
          <span class = "h-[3px] w-full bg-white rotate-45 relative top-[9px]"></span>
          <span class = "h-[3px] w-full bg-white opacity-0"></span>
          <span class = "h-[3px] w-full bg-white relative bottom-3 rotate-[-45deg]"></span>
        </div>
    </header>

    <main class = "p-4 flex bg-sky-200 h-screen">
        <slot />
    </main>

    <footer class = "flex flex-row w-full bg-gray-900 border-t-2 border-cyan-400 items-center justify-center px-4 py-2 gap-4">
        <a href = "https://www.youtube.com/"><img src="assets/images/yt.png" class = "w-16 h-16"></a>
        <a href = "https://github.com/"><img src="assets/images/github4.png" class = "w-16 h-16 transparent"></a>
        <a href = "https://www.facebook.com/"><img src="assets/images/facebook.png" class = "w-16 h-16 transparent"></a>
    </footer>
</template>

<script setup lang = 'ts'>
import { useHead } from '#app';
import {ref} from 'vue'

useHead({
  script: [
    {
      async: true,
      src: 'https://www.googletagmanager.com/gtag/js?id=G-WSCV6FX8J1',
    },
    {
      innerHTML: `
        window.dataLayer = window.dataLayer || [];
        function gtag(){dataLayer.push(arguments);}
        gtag('js', new Date());
        gtag('config', 'G-WSCV6FX8J1');
      `,
      type: 'text/javascript',
    },
  ],
  __dangerouslyDisableSanitizersByTagID: {
    gtag: ['innerHTML'],
  },
});

const burger = ref<boolean>(false)
const submenu = ref<boolean>(false)

const switch_burger = () => {burger.value = !burger.value}
const switch_submenu = () => {submenu.value = !submenu.value}

</script>