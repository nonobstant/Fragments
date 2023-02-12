<template>
  <div class="bg-gray-200 dark:bg-gray-900 dark:text-white min-h-screen text-center pt-5 transition duration-700 ease-in-out">
    <svg v-if='theme ==="light"'  @click="themeDark" class="w-10 h-10 inline cursor-crosshair p-2 hover:text-white hover:bg-black rounded-lg" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
     <path d="M17.293 13.293A8 8 0 016.707 2.707a8.001 8.001 0 1010.586 10.586z"></path>
    </svg>
    <svg v-else  @click="themeLight" class="w-10 h-10 inline cursor-crosshair p-2 hover:text-black hover:bg-white rounded-lg" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
     <path d="M17.293 13.293A8 8 0 016.707 2.707a8.001 8.001 0 1010.586 10.586z"></path>
    </svg>
    <router-view></router-view>
    
  </div>
  
</template>

<script>
export default {
  data() {
    return {
      theme : ""
    }
  },
  methods : {
    // Theme action
    themeLight() {
      document.documentElement.classList.remove("dark");
      localStorage.theme = "light";
      this.theme = "light";
    },
    themeDark() {
      document.documentElement.classList.add("dark");
      localStorage.theme = "dark";
      this.theme = "dark";
    },
  },
  mounted() {
    //theme setup
    if (
      localStorage.theme === "dark" ||
      (!("theme" in localStorage) &&
        window.matchMedia("(prefers-color-scheme: dark)").matches)
    ) {
      document.documentElement.classList.add("dark");
      this.theme = "dark";
    } else {
      document.documentElement.classList.remove("dark");
      this.theme = "light";
    }
  }
}
</script>

<style>
</style>
