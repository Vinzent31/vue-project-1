<template>
    <nav class="absolute top-0 left-0 z-20 w-full px-6 py-4 fixed">
        <div class="mx-auto flex max-w-7xl items-center justify-between">
            
            <!-- Logo Section -->
            <div class="flex items-center">
                <a href="#" class="flex flex-col">
                    <span class="text-2xl font-black tracking-wider text-white drop-shadow-md pl-7">
                        POKÉMON
                    </span>
                    <span class="text-[10px] font-bold tracking-[0.3em] text-emerald-300 drop-shadow pl-7">
                        LEAFGREEN
                    </span>
                </a>
            </div>

            <!-- Floating Pill Navigation Bar -->
            <div class="hidden items-center gap-6 rounded-full border border-emerald-500/20 bg-emerald-950/40 px-6 py-2.5 backdrop-blur-md shadow-lg md:flex mr-17">
                
                <!-- Menu Links -->
                <div class="flex items-center gap-6 text-sm font-semibold text-emerald-100/90">
                    <a href="#home" class="transition hover:text-white">
                        Home
                    </a>
                    <a href="#about" class="transition hover:text-white">
                        About
                    </a>
                    <a href="#starters" class="transition hover:text-white">
                        Starters
                    </a>
                    <a href="#gameplay" class="transition hover:text-white">
                        Gameplay
                    </a>
                </div>

                <!-- CTA Button (Start Journey) -->
                <a
                    href="#start"
                    class="rounded-full bg-gradient-to-r from-emerald-600 to-emerald-500 px-5 py-2 text-sm font-bold text-white shadow-md transition duration-300 hover:from-emerald-500 hover:to-emerald-400 hover:shadow-emerald-500/20"
                >
                    Start Journey
                </a>

                <!-- Icons (Search & User Profile) -->
                <div class="flex items-center gap-3 border-l border-emerald-500/20 pl-4 text-emerald-100">
                    <!-- Search Icon -->
                    <button aria-label="Search" class="p-1 transition hover:text-white">
                        <svg class="h-5 w-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"/>
                        </svg>
                    </button>

                    <!-- Profile Icon -->
                    <button aria-label="Profile" class="p-1 transition hover:text-white">
                        <svg class="h-5 w-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"/>
                        </svg>
                    </button>
                </div>

            </div>

            <!-- Mobile Button -->
            <button
                class="rounded-xl border border-emerald-500/30 bg-emerald-950/60 p-2.5 text-white backdrop-blur-md transition hover:bg-emerald-900/60 md:hidden"
                aria-label="Toggle Menu"
            >
                <svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/>
                </svg>
            </button>

        </div>
    </nav>
</template>