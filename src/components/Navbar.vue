<template>
  <nav class="bg-gray-900/70 text-gray-100 p-4 flex justify-between items-center shadow-md backdrop-blur-md fixed w-full z-50">
    <!-- Logo -->
    <div class="flex items-center space-x-2">
      <img src="@/assets/img/icon.ico" alt="Logo" class="h-10 w-10 object-cover rounded-full logo-glow">
      <span class="text-xl font-bold tracking-wide logo-glow-text">&lt;Mattéouti-Portfolio/&gt;</span>
    </div>

    <!-- Burger Button (mobile only) -->
    <button 
      @click="isOpen = !isOpen" 
      class="md:hidden focus:outline-none"
    >
      <svg v-if="!isOpen" xmlns="http://www.w3.org/2000/svg" class="h-7 w-7" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
      </svg>
      <svg v-else xmlns="http://www.w3.org/2000/svg" class="h-7 w-7" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
      </svg>
    </button>

    <!-- Navigation Links (desktop) -->
    <ul class="hidden md:flex space-x-6">
      <li v-for="link in links" :key="link.to">
        <router-link 
          :to="link.to" 
          class="relative group text-white transition-all duration-300 hover:text-yellow-400 hover-glow"
        >
          {{ link.label }}
          <span class="absolute left-0 -bottom-1 w-0 h-0.5 bg-yellow-400 transition-all group-hover:w-full"></span>
        </router-link>
      </li>
    </ul>

    <!-- Mobile Menu -->
    <transition name="fade">
      <ul 
        v-if="isOpen" 
        class="absolute top-16 left-0 w-full bg-gray-900/95 backdrop-blur-md flex flex-col space-y-4 p-6 md:hidden shadow-lg"
      >
        <li v-for="link in links" :key="link.to">
          <router-link 
            :to="link.to" 
            class="block py-2 text-lg text-white hover:text-yellow-400 transition hover-glow"
            @click="isOpen = false"
          >
            {{ link.label }}
          </router-link>
        </li>
      </ul>
    </transition>
  </nav>
</template>

<script setup>
import { ref } from "vue";

const isOpen = ref(false);

const links = [
  { to: "/", label: "Home" },
  { to: "/about", label: "About" },
  { to: "/portfolio", label: "Portfolio" },
  { to: "/services", label: "Services" },
  { to: "/contact", label: "Contact" },
];
</script>

<style>
/* Glow pour logo et texte */
.logo-glow {
  box-shadow: 0 0 8px rgba(250, 204, 21, 0.7);
  transition: all 0.3s ease-in-out;
}
.logo-glow:hover {
  box-shadow: 0 0 15px rgba(250, 204, 21, 1);
}

.logo-glow-text {
  text-shadow: 0 0 5px rgba(250, 204, 21, 0.7);
  transition: all 0.3s ease-in-out;
}
.logo-glow-text:hover {
  text-shadow: 0 0 12px rgba(250, 204, 21, 1);
}

/* Glow pour liens */
.hover-glow:hover {
  text-shadow: 0 0 8px rgba(250, 204, 21, 0.8);
}
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}
</style>
