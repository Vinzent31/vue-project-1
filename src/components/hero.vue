<template>
    <section
        id="home"
        class="relative min-h-screen overflow-hidden bg-green-950"
    >

        <!-- Background -->
        <div
            class="absolute inset-0 bg-cover bg-center"
            style="background-image: url('/src/assets/images/oke.jfif')"
        ></div>

        <!-- Overlay -->
        <div
            class="absolute inset-0 bg-gradient-to-r
            from-black/70
            via-black/40
            to-transparent"
        ></div>

        <!-- Content -->
        <div
            class="relative z-10 mx-auto flex min-h-screen
            max-w-7xl items-center px-6"
        >

            <div class="max-w-xl">


                <!-- Main Heading -->
                <h1
                    class="text-4xl font-black leading-tight
                    text-white sm:text-5xl md:text-6xl"
                >
                    Uncover the
                    <span class="block text-yellow-300">
                        Mysteries
                    </span>

                    <span class="block">
                        of the Wild!
                    </span>
                </h1>

                <!-- Description -->
                <p
                    class="mt-6 max-w-lg text-base
                    leading-relaxed text-white/90 md:text-lg"
                >
                    A new adventure awaits in an unexplored world.
                    Discover new creatures, explore beautiful landscapes,
                    and build your own adventure.
                </p>

                <!-- Button -->
                <div class="mt-8 flex flex-wrap gap-4">

                    <a
                        href="#explore"
                        class="rounded-full bg-yellow-400
                        px-6 py-3 text-sm font-bold
                        text-green-950 shadow-lg
                        transition duration-300
                        hover:-translate-y-1
                        hover:bg-yellow-300"
                    >
                        Begin Your Adventure
                        <span class="ml-2">→</span>
                    </a>

                    <a
                        href="#discover"
                        class="rounded-full border
                        border-white/50
                        bg-white/10
                        px-6 py-3 text-sm font-semibold
                        text-white backdrop-blur-md
                        transition duration-300
                        hover:bg-white/20"
                    >
                        Discover More
                    </a>

                </div>                

            </div>

        </div>

        <!-- Bottom Gradient -->
        <div
            class="absolute bottom-0 left-0 h-32 w-full
            bg-gradient-to-t from-green-950
            to-transparent"
        ></div>

    </section>
</template>