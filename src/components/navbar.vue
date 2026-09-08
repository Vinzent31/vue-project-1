<script setup>
import { ref } from 'vue'

// State untuk mengatur buka/tutup menu mobile
const isMenuOpen = ref(false)

// Function untuk toggle state
const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

// Function untuk menutup menu saat link diklik
const closeMenu = () => {
  isMenuOpen.value = false
}
</script>

<template>
  <nav class="fixed top-0 left-0 z-50 w-full px-6 py-4">
    <div class="mx-auto flex max-w-7xl items-center justify-between">
      
      <!-- Logo Section -->
      <div class="flex items-center">
        <a href="#" class="flex flex-col">
          <span class="text-2xl font-black tracking-wider text-white drop-shadow-md">
            POKÉMON
          </span>
          <span class="text-[10px] font-bold tracking-[0.3em] text-emerald-300 drop-shadow">
            LEAFGREEN
          </span>
        </a>
      </div>

      <!-- Floating Pill Navigation Bar (Desktop) -->
      <div class="hidden items-center gap-6 rounded-full border border-emerald-500/20 bg-emerald-950/40 px-6 py-2.5 backdrop-blur-md shadow-lg md:flex">
        
        <!-- Menu Links -->
        <div class="flex items-center gap-6 text-sm font-semibold text-emerald-100/90">
          <a href="#home" class="transition hover:text-white">Home</a>
          <a href="#about" class="transition hover:text-white">About</a>
          <a href="#starters" class="transition hover:text-white">Starters</a>
          <a href="#gameplay" class="transition hover:text-white">Gameplay</a>
        </div>

        <!-- CTA Button -->
        <a
          href="#start"
          class="rounded-full bg-gradient-to-r from-emerald-600 to-emerald-500 px-5 py-2 text-sm font-bold text-white shadow-md transition duration-300 hover:from-emerald-500 hover:to-emerald-400 hover:shadow-emerald-500/20"
        >
          Start Journey
        </a>

        <!-- Icons (Search & User Profile) -->
        <div class="flex items-center gap-3 border-l border-emerald-500/20 pl-4 text-emerald-100">
          <button aria-label="Search" class="p-1 transition hover:text-white">
            <svg class="h-5 w-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"/>
            </svg>
          </button>

          <button aria-label="Profile" class="p-1 transition hover:text-white">
            <svg class="h-5 w-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"/>
            </svg>
          </button>
        </div>

      </div>

      <!-- Mobile Button (Hamburger / Close Icon) -->
      <button
        @click="toggleMenu"
        class="rounded-xl border border-emerald-500/30 bg-emerald-950/60 p-2.5 text-white backdrop-blur-md transition hover:bg-emerald-900/60 md:hidden focus:outline-none"
        aria-label="Toggle Menu"
      >
        <!-- Icon Hamburger (Saat Tertutup) -->
        <svg v-if="!isMenuOpen" class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/>
        </svg>

        <!-- Icon X / Close (Saat Terbuka) -->
        <svg v-else class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
        </svg>
      </button>

    </div>

    <!-- Mobile Dropdown Menu (Muncul Saat isMenuOpen = true) -->
    <transition
      enter-active-class="transition duration-200 ease-out"
      enter-from-class="opacity-0 -translate-y-4"
      enter-to-class="opacity-100 translate-y-0"
      leave-active-class="transition duration-150 ease-in"
      leave-from-class="opacity-100 translate-y-0"
      leave-to-class="opacity-0 -translate-y-4"
    >
      <div 
        v-if="isMenuOpen" 
        class="mt-3 flex flex-col gap-4 rounded-2xl border border-emerald-500/20 bg-emerald-950/90 p-5 backdrop-blur-lg shadow-xl md:hidden"
      >
        <!-- Links Mobile -->
        <div class="flex flex-col gap-3 text-base font-semibold text-emerald-100">
          <a href="#home" @click="closeMenu" class="transition hover:text-white">Home</a>
          <a href="#about" @click="closeMenu" class="transition hover:text-white">About</a>
          <a href="#starters" @click="closeMenu" class="transition hover:text-white">Starters</a>
          <a href="#gameplay" @click="closeMenu" class="transition hover:text-white">Gameplay</a>
        </div>

        <hr class="border-emerald-500/20" />

        <!-- Actions Mobile (Search, Profile, CTA) -->
        <div class="flex items-center justify-between gap-4">
          <div class="flex items-center gap-3 text-emerald-100">
            <button aria-label="Search" class="p-1 transition hover:text-white">
              <svg class="h-5 w-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"/>
              </svg>
            </button>
            <button aria-label="Profile" class="p-1 transition hover:text-white">
              <svg class="h-5 w-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"/>
              </svg>
            </button>
          </div>

          <a
            href="#start"
            @click="closeMenu"
            class="rounded-full bg-gradient-to-r from-emerald-600 to-emerald-500 px-5 py-2 text-center text-sm font-bold text-white shadow-md transition duration-300 hover:from-emerald-500 hover:to-emerald-400"
          >
            Start Journey
          </a>
        </div>
      </div>
    </transition>
  </nav>
</template>