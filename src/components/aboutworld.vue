<template>
  <section
    id="about"
    class="relative min-h-screen bg-transparent px-6 py-24"
  >
    <div
      class="mx-auto flex min-h-[600px] max-w-6xl items-center justify-center"
    >
      <!-- =================================================
           ABOUT CARD (Dengan Bingkai & Dekorasi Minimalis)
      ================================================== -->
      <div
        class="relative w-full overflow-hidden
               rounded-[28px]
               border border-emerald-900/20
               bg-[#D8E5E2]
               shadow-[0_25px_80px_rgba(0,0,0,0.3)]
               ring-1 ring-white/40
               md:min-h-[520px]"
      >

        <!-- =================================================
             MINIMALIST BORDER & CORNER DECORATIONS
        ================================================== -->
        <!-- Garis Aksen Gradient Atas & Bawah -->
        <div class="pointer-events-none absolute inset-x-12 top-0 h-[2px] bg-gradient-to-r from-transparent via-emerald-600/40 to-transparent"></div>
        <div class="pointer-events-none absolute inset-x-12 bottom-0 h-[2px] bg-gradient-to-r from-transparent via-emerald-600/40 to-transparent"></div>

        <!-- Aksen Bracket Sudut Minimalis (Top-Left) -->
        <div class="pointer-events-none absolute left-4 top-4 h-4 w-4 border-l-2 border-t-2 border-emerald-800/40"></div>
        <!-- Aksen Bracket Sudut Minimalis (Bottom-Left) -->
        <div class="pointer-events-none absolute bottom-4 left-4 h-4 w-4 border-b-2 border-l-2 border-emerald-800/40"></div>
        <!-- Aksen Bracket Sudut Minimalis (Bottom-Right) -->
        <div class="pointer-events-none absolute bottom-4 right-4 h-4 w-4 border-b-2 border-r-2 border-emerald-800/40"></div>

        <!-- Decorative Glow Background -->
        <div
          class="pointer-events-none absolute
                 -left-20 -top-20
                 h-60 w-60
                 rounded-full
                 bg-emerald-400/20
                 blur-3xl"
        ></div>

        <div
          class="pointer-events-none absolute
                 -bottom-24 -right-20
                 h-72 w-72
                 rounded-full
                 bg-emerald-300/20
                 blur-3xl"
        ></div>

        <!-- =================================================
             CONTENT
        ================================================== -->
        <div
          class="relative z-10 grid min-h-[500px]
                 grid-cols-1
                 items-center
                 md:grid-cols-2"
        >
          <!-- =================================================
               LEFT : POKEMON IMAGE
          ================================================== -->
          <div
            class="relative flex
                   min-h-[400px]
                   items-center
                   justify-center
                   p-4
                   md:min-h-[520px]"
          >
            <!-- Decorative circle outer -->
            <div
              class="absolute
                     h-[300px] w-[300px]
                     rounded-full
                     border border-emerald-900/15
                     sm:h-[360px] sm:w-[360px]
                     md:h-[400px] md:w-[400px]"
            ></div>

            <!-- Decorative circle inner -->
            <div
              class="absolute
                     h-[220px] w-[220px]
                     rounded-full
                     border border-emerald-900/15
                     sm:h-[280px] sm:w-[280px]
                     md:h-[310px] md:w-[310px]"
            ></div>

            <!-- POKEMON IMAGE -->
            <img
              src="/src/assets/images/aabout.png"
              alt="Pokemon"
              class="about-pokemon
                     relative z-10
                     h-auto
                     w-[320px]
                     max-w-[95%]
                     object-contain
                     drop-shadow-[0_25px_25px_rgba(0,0,0,0.3)]
                     transition-transform duration-300 hover:scale-105
                     sm:w-[380px]
                     md:w-[430px]
                     
                     ml-30
                     mb-12"
            />

            <!-- Ground shadow -->
            <div
              class="absolute bottom-[35px]
                     h-6 w-64
                     rounded-[50%]
                     bg-black/20
                     blur-md
                     md:bottom-[45px]"
            ></div>
          </div>

          <!-- =================================================
               RIGHT : ABOUT INFORMATION
          ================================================== -->
          <div
            class="flex flex-col
                   justify-center
                   px-8 pb-12 pt-4
                   text-center
                   md:px-12
                   md:py-10
                   md:text-left
                   lg:px-16"
          >
            <!-- Small label -->
            <span
              class="mb-3 text-xs
                     font-extrabold uppercase
                     tracking-[0.35em]
                     text-emerald-800"
            >
              Discover The World
            </span>

            <!-- Main Title -->
            <h2
              class="text-5xl
                     font-black uppercase
                     leading-none
                     tracking-tight
                     text-[#082820]
                     sm:text-6xl
                     lg:text-7xl"
            >
              About
            </h2>

            <!-- Subtitle -->
            <h3
              class="mt-3 text-2xl
                     font-bold
                     text-[#082820]
                     sm:text-3xl"
            >
              The LeafGreen World
            </h3>

            <!-- Divider -->
            <div
              class="mx-auto my-6
                     h-1.5 w-16
                     rounded-full
                     bg-emerald-500
                     md:mx-0"
            ></div>

            <!-- Description -->
            <p
              class="max-w-lg
                     text-sm
                     font-medium
                     leading-relaxed
                     text-emerald-950/80
                     sm:text-base"
            >
              Welcome to a world filled with nature, mysterious creatures, and
              unforgettable adventures. Explore the world of LeafGreen and discover
              what awaits beyond every path.
            </p>

            <p
              class="mt-4 max-w-lg
                     text-sm
                     font-medium
                     leading-relaxed
                     text-emerald-950/70"
            >
              From peaceful forests to exciting journeys, every place has its own
              story waiting to be discovered.
            </p>

            <!-- MINI INFO / BADGES -->
            <div
              class="mt-8 flex flex-wrap
                     justify-center gap-3
                     md:justify-start"
            >
              <div
                class="rounded-full
                       border border-emerald-800/20
                       bg-emerald-900/10
                       px-4 py-2"
              >
                <span
                  class="text-[11px]
                         font-bold uppercase
                         tracking-widest
                         text-emerald-900"
                >
                  Nature
                </span>
              </div>

              <div
                class="rounded-full
                       border border-emerald-800/20
                       bg-emerald-900/10
                       px-4 py-2"
              >
                <span
                  class="text-[11px]
                         font-bold uppercase
                         tracking-widest
                         text-emerald-900"
                >
                  Adventure
                </span>
              </div>

              <div
                class="rounded-full
                       border border-emerald-800/20
                       bg-emerald-900/10
                       px-4 py-2"
              >
                <span
                  class="text-[11px]
                         font-bold uppercase
                         tracking-widest
                         text-emerald-900"
                >
                  Discovery
                </span>
              </div>
            </div>

            <!-- CTA BUTTON -->
            <div class="mt-8">
              <button
                class="group inline-flex
                       items-center gap-4
                       rounded-full
                       bg-[#063c2e]
                       px-7 py-3.5
                       text-xs
                       font-bold uppercase
                       tracking-wider
                       text-white
                       shadow-md
                       transition-all
                       duration-300
                       hover:-translate-y-1
                       hover:bg-emerald-700
                       hover:shadow-xl
                       hover:shadow-emerald-900/30"
              >
                <span>Explore More</span>
                <span
                  class="text-lg
                         transition-transform
                         duration-300
                         group-hover:translate-x-1"
                >
                  →
                </span>
              </button>
            </div>
          </div>
        </div>

        <!-- CARD CORNER DECORATION (Top-Right) -->
        <div
          class="absolute right-5 top-5
                 flex items-center gap-1.5"
        >
          <span class="h-2 w-2 rounded-full bg-emerald-700"></span>
          <span class="h-2 w-2 rounded-full bg-emerald-700/40"></span>
          <span class="h-2 w-2 rounded-full bg-emerald-700/20"></span>
        </div>
      </div>
    </div>

    
  </section>
</template>