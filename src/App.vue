<script setup>
import { onMounted, ref } from 'vue';

const isDark = ref(false)

const ToogleDark = () => {
  isDark.value = !isDark.value
  if (isDark.value) {
    document.documentElement.classList.add('dark')
    localStorage.setItem('theme' , 'dark')
  }else {
    document.documentElement.classList.remove('dark')
    localStorage.setItem('theme' , 'light')
  }
}

onMounted(()=> {
  const storedTheme = localStorage.getItem('theme')
  if (storedTheme) {
    isDark.value = storedTheme == 'dark'
  }else {
    isDark.value = window.matchMedia('(prefers-color-scheme: dark)').matches
  }

  document.documentElement.classList.toggle('dark' , isDark.value)
})
</script>


<template>
  <header class="  justify-center items-center h-screen w-full dark:bg-black bg-white dark:text-white text-black flex ">
    <button @click="ToogleDark" class="h-[40px] w-[200px] bg-sky-400 rounded-full font-medium text-white">
      value:{{ isDark }}
    </button>
  </header>
</template>


<style scoped>

</style>
