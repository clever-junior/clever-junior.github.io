<script setup lang="ts">
import { ref } from 'vue';
import { RouterLink, RouterView } from 'vue-router';

const showMenu = ref(false);

const handleMenu = () => {
  showMenu.value = !showMenu.value; 
}
</script>

<template>
  <header class="flex justify-center items-center w-full h-16 bg-blue-950 text-white">
    <div class="flex items-center w-11/12 max-sm:justify-between mt-2 ml-2">
      <h1 class="font-bold text-4xl pb-3">Clever Junior</h1>
      
      <section v-bind:class="showMenu ? 'max-sm:bg-blue-950 max-sm:absolute max-sm:top-0 max-sm:left-0 max-sm:z-10 max-sm:flex max-sm:justify-center max-sm:items-center max-sm:w-full max-sm:h-full' : 'ml-14'">
        <button type="button" v-on:click="handleMenu" class="sm:hidden w-9 h-8" v-bind:class="showMenu && 'absolute right-4 top-4'"> 
          <div v-bind:class="showMenu && 'rotate-45 translate-x-2 translate-y-2 transition-all'" class="bg-white h-2 w-full my-1 mx-auto rounded-full"></div>
          <div v-bind:class="showMenu && 'opacity-0 transition-all'" class="bg-white h-2 w-full my-1 mx-auto rounded-full"></div>
          <div v-bind:class="showMenu && 'transition-all -rotate-45 translate-x-2 -translate-y-4'" class="bg-white h-2 w-full my-1 mx-auto rounded-full"></div>
        </button>
        <nav v-bind:class="showMenu ? 'max-sm:block text-center transition-all text-4xl' : 'max-sm:hidden'">
          <ul class="flex gap-3 font-medium text-lg" v-bind:class="showMenu && 'max-sm:text-center max-sm:block max-sm:transition-all max-sm:text-4xl'">
            <li>
              <RouterLink to="/" v-bind:class="showMenu && 'block transition-all text-4xl'">Home</RouterLink>
            </li>
            <li>
              <RouterLink to="/about" v-bind:class="showMenu && 'block transition-transform text-4xl'">About</RouterLink>
            </li>
          </ul>
        </nav>
      </section>
    </div>
  </header>

  <RouterView />
</template>

<style scoped></style>
