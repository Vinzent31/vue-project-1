<script setup>

import { ref, computed, onMounted, onBeforeUnmount } from 'vue'
import Pokemon3D from './pokemon3D.vue'


// ======================================================
// STARTER DATA
// ======================================================

const starters = [

    {
        id: 1,
        dex: '#001',
        name: 'BULBASAUR',

        model: '/models/bulbasaur.glb',

        animate: false,
        autoRotate: true,

        description:
            'A mysterious seed was planted on its back at birth. The seed grows together with this Pokémon.',

        types: [
            {
                name: 'GRASS',
                icon: '🌿',
                color: 'emerald'
            },
            {
                name: 'POISON',
                icon: '☠️',
                color: 'purple'
            }
        ],

        stats: {
            hp: 45,
            attack: 49,
            defense: 49,
            speed: 45
        },

        accent: 'emerald',
        accentText: 'text-emerald-400',
        accentBg: 'bg-emerald-500',
        accentBorder: 'border-emerald-400/30',

        accentGlow:
            'shadow-[0_0_50px_rgba(16,185,129,0.15)]',

        total: 188
    },


    // ==================================================
    // CHARMANDER
    // ==================================================

    {
        id: 4,
        dex: '#004',
        name: 'CHARMANDER',

        model: '/models/charmander.glb',
        modelScale: 1.5,

        description:
            'A small Fire-type Pokémon with a flame burning brightly at the tip of its tail.',

        types: [
            {
                name: 'FIRE',
                icon: '🔥',
                color: 'orange'
            }
        ],

        stats: {
            hp: 39,
            attack: 52,
            defense: 43,
            speed: 65
        },

        accent: 'orange',
        accentText: 'text-orange-400',
        accentBg: 'bg-orange-500',
        accentBorder: 'border-orange-400/30',

        accentGlow:
            'shadow-[0_0_50px_rgba(249,115,22,0.15)]',

        total: 199
    },


    // ==================================================
    // SQUIRTLE
    // ==================================================

    {
        id: 7,
        dex: '#007',
        name: 'SQUIRTLE',

        model: '/models/squirtle.glb',
        modelScale: 1.2,

        description:
            'A tiny Water-type Pokémon with a strong shell that protects its body from danger.',

        types: [
            {
                name: 'WATER',
                icon: '💧',
                color: 'cyan'
            }
        ],

        stats: {
            hp: 44,
            attack: 48,
            defense: 65,
            speed: 43
        },

        accent: 'cyan',
        accentText: 'text-cyan-400',
        accentBg: 'bg-cyan-500',
        accentBorder: 'border-cyan-400/30',

        accentGlow:
            'shadow-[0_0_50px_rgba(6,182,212,0.15)]',

        total: 200
    }

]


// ======================================================
// CURRENT INDEX
// ======================================================

const currentIndex = ref(0)


// ======================================================
// CURRENT STARTER
// ======================================================

const currentStarter = computed(() => {
    return starters[currentIndex.value]
})


// ======================================================
// CHANGING STATE
// ======================================================

const isChanging = ref(false)


// ======================================================
// CHANGE STARTER
// ======================================================

function changeStarter(index) {

    if (index === currentIndex.value) {
        return
    }

    if (isChanging.value) {
        return
    }

    isChanging.value = true

    currentIndex.value = index

    setTimeout(() => {
        isChanging.value = false
    }, 500)

}


// ======================================================
// NEXT
// ======================================================

function nextStarter() {

    const next =
        (currentIndex.value + 1) %
        starters.length

    changeStarter(next)

}


// ======================================================
// PREVIOUS
// ======================================================

function previousStarter() {

    const previous =
        (currentIndex.value - 1 + starters.length) %
        starters.length

    changeStarter(previous)

}


// ======================================================
// KEYBOARD
// ======================================================

function handleKeyboard(event) {

    if (event.key === 'ArrowRight') {
        nextStarter()
    }

    if (event.key === 'ArrowLeft') {
        previousStarter()
    }

}


// ======================================================
// MOUNT
// ======================================================

onMounted(() => {

    window.addEventListener(
        'keydown',
        handleKeyboard
    )

})


// ======================================================
// UNMOUNT
// ======================================================

onBeforeUnmount(() => {

    window.removeEventListener(
        'keydown',
        handleKeyboard
    )

})

</script>


<template>

<section
    class="
        relative
        min-h-screen
        overflow-hidden
        bg-transparent
        text-white
    "
>


    <!-- ================================================== -->
    <!-- BACKGROUND -->
    <!-- ================================================== -->

    <div
        class="
            pointer-events-none
            absolute
            -left-40
            top-20
            h-[500px]
            w-[500px]
            rounded-full
            bg-emerald-500/10
            blur-[140px]
        "
    ></div>


    <div
        class="
            pointer-events-none
            absolute
            -right-40
            bottom-0
            h-[500px]
            w-[500px]
            rounded-full
            bg-emerald-400/10
            blur-[140px]
        "
    ></div>


    <!-- GRID -->

    <div
        class="
            pointer-events-none
            absolute
            inset-0
            opacity-[0.025]
        "
        style="
            background-image:
                linear-gradient(
                    rgba(255,255,255,0.4) 1px,
                    transparent 1px
                ),
                linear-gradient(
                    90deg,
                    rgba(255,255,255,0.4) 1px,
                    transparent 1px
                );
            background-size: 50px 50px;
        "
    ></div>


    <!-- ================================================== -->
    <!-- CONTAINER -->
    <!-- ================================================== -->

    <div
        class="
            relative
            z-10
            mx-auto
            max-w-[1400px]
            px-6
            py-16
            lg:px-10
            xl:py-20
        "
    >


        <!-- ================================================== -->
        <!-- HEADER -->
        <!-- ================================================== -->

        <div
            class="
                mb-10
                max-w-2xl
            "
        >

            <div
                class="
                    mb-4
                    flex
                    items-center
                    gap-2
                    text-sm
                    font-bold
                    uppercase
                    tracking-[0.25em]
                    text-emerald-400
                "
            >

                <span>✦</span>

                Pick Your Starter

            </div>


            <h1
                class="
                    text-4xl
                    font-black
                    leading-[1.05]
                    tracking-tight
                    sm:text-5xl
                    lg:text-6xl
                "
            >

                Choose your

                <span class="text-emerald-400">
                    first partner.
                </span>

            </h1>


            <p
                class="
                    mt-5
                    max-w-xl
                    text-sm
                    leading-7
                    text-white/50
                    sm:text-base
                "
            >

                Every adventure begins with a choice.
                Find the starter that will accompany you
                on your journey.

            </p>

        </div>



        <!-- ================================================== -->
        <!-- MAIN GRID -->
        <!-- ================================================== -->

        <div
            class="
                grid
                gap-5
                lg:grid-cols-[390px_minmax(0,1fr)]
                xl:grid-cols-[420px_minmax(0,1fr)]
            "
        >


            <!-- ================================================== -->
            <!-- LEFT INFORMATION PANEL -->
            <!-- ================================================== -->

            <div
                class="
                    relative
                    flex
                    flex-col
                    overflow-hidden
                    rounded-[22px]
                    border
                    border-[#123C30]
                    bg-[#071C16]
                    p-7
                    shadow-[0_20px_60px_rgba(0,0,0,0.18)]
                "
            >

                <!-- TOP ACCENT -->

                <div
                    class="
                        absolute
                        left-0
                        right-0
                        top-0
                        h-px
                        bg-emerald-400/40
                    "
                ></div>


                <!-- TOP DECORATION -->

                <div
                    class="
                        absolute
                        right-7
                        top-7
                        flex
                        items-center
                        gap-2
                    "
                >

                    <span
                        class="
                            h-2
                            w-2
                            animate-pulse
                            rounded-full
                            bg-emerald-400
                        "
                    ></span>

                    <span
                        class="
                            text-[10px]
                            font-bold
                            uppercase
                            tracking-widest
                            text-white/30
                        "
                    >
                        Active
                    </span>

                </div>



                <!-- ================================================== -->
                <!-- POKEMON NAME -->
                <!-- ================================================== -->

                <Transition
                    name="content"
                    mode="out-in"
                >

                    <div
                        :key="currentStarter.id"
                        class="mb-6"
                    >

                        <p
                            :class="[
                                'mb-2 text-sm font-bold tracking-[0.25em]',
                                currentStarter.accentText
                            ]"
                        >
                            {{ currentStarter.dex }}
                        </p>


                        <h2
                            class="
                                text-3xl
                                font-black
                                tracking-tight
                                sm:text-4xl
                            "
                        >
                            {{ currentStarter.name }}
                        </h2>

                    </div>

                </Transition>



                <!-- ================================================== -->
                <!-- TYPE BADGES -->
                <!-- ================================================== -->

                <Transition
                    name="content"
                    mode="out-in"
                >

                    <div
                        :key="`${currentStarter.id}-types`"
                        class="
                            mb-6
                            flex
                            flex-wrap
                            gap-2
                        "
                    >

                        <span
                            v-for="type in currentStarter.types"
                            :key="type.name"
                            :class="[
                                'flex items-center gap-2 rounded-lg px-3 py-2 text-xs font-bold ring-1',

                                type.color === 'emerald'
                                    ? 'bg-emerald-500/10 text-emerald-400 ring-emerald-400/20'
                                    : '',

                                type.color === 'purple'
                                    ? 'bg-purple-500/10 text-purple-300 ring-purple-400/20'
                                    : '',

                                type.color === 'orange'
                                    ? 'bg-orange-500/10 text-orange-400 ring-orange-400/20'
                                    : '',

                                type.color === 'cyan'
                                    ? 'bg-cyan-500/10 text-cyan-400 ring-cyan-400/20'
                                    : ''
                            ]"
                        >

                            <span>
                                {{ type.icon }}
                            </span>

                            {{ type.name }}

                        </span>

                    </div>

                </Transition>



                <!-- ================================================== -->
                <!-- DESCRIPTION -->
                <!-- ================================================== -->

                <Transition
                    name="content"
                    mode="out-in"
                >

                    <p
                        :key="`${currentStarter.id}-description`"
                        class="
                            mb-8
                            min-h-[72px]
                            text-sm
                            leading-7
                            text-white/45
                        "
                    >

                        {{ currentStarter.description }}

                    </p>

                </Transition>



                <!-- DIVIDER -->

                <div
                    class="
                        mb-7
                        h-px
                        bg-[#123C30]
                    "
                ></div>



                <!-- ================================================== -->
                <!-- STATS -->
                <!-- ================================================== -->

                <Transition
                    name="content"
                    mode="out-in"
                >

                    <div
                        :key="`${currentStarter.id}-stats`"
                        class="mb-8"
                    >

                        <div
                            class="
                                mb-6
                                flex
                                items-center
                                justify-between
                            "
                        >

                            <h3
                                :class="[
                                    'text-xs font-bold uppercase tracking-[0.2em]',
                                    currentStarter.accentText
                                ]"
                            >
                                Base Stats
                            </h3>


                            <span
                                class="
                                    text-[10px]
                                    font-bold
                                    tracking-widest
                                    text-white/25
                                "
                            >
                                TOTAL {{ currentStarter.total }}
                            </span>

                        </div>



                        <!-- HP -->

                        <div class="mb-5">

                            <div
                                class="
                                    mb-2
                                    flex
                                    justify-between
                                    text-xs
                                "
                            >

                                <span class="text-white/60">
                                    HP
                                </span>

                                <span class="font-bold text-white/70">
                                    {{ currentStarter.stats.hp }}
                                </span>

                            </div>


                            <div
                                class="
                                    h-1.5
                                    overflow-hidden
                                    rounded-full
                                    bg-[#0D3025]
                                "
                            >

                                <div
                                    :class="[
                                        'stat-bar h-full rounded-full',
                                        currentStarter.accentBg
                                    ]"
                                    :style="{
                                        width:
                                            `${currentStarter.stats.hp}%`
                                    }"
                                ></div>

                            </div>

                        </div>



                        <!-- ATTACK -->

                        <div class="mb-5">

                            <div
                                class="
                                    mb-2
                                    flex
                                    justify-between
                                    text-xs
                                "
                            >

                                <span class="text-white/60">
                                    Attack
                                </span>

                                <span class="font-bold text-white/70">
                                    {{ currentStarter.stats.attack }}
                                </span>

                            </div>


                            <div
                                class="
                                    h-1.5
                                    overflow-hidden
                                    rounded-full
                                    bg-[#0D3025]
                                "
                            >

                                <div
                                    :class="[
                                        'stat-bar h-full rounded-full',
                                        currentStarter.accentBg
                                    ]"
                                    :style="{
                                        width:
                                            `${currentStarter.stats.attack}%`
                                    }"
                                ></div>

                            </div>

                        </div>



                        <!-- DEFENSE -->

                        <div class="mb-5">

                            <div
                                class="
                                    mb-2
                                    flex
                                    justify-between
                                    text-xs
                                "
                            >

                                <span class="text-white/60">
                                    Defense
                                </span>

                                <span class="font-bold text-white/70">
                                    {{ currentStarter.stats.defense }}
                                </span>

                            </div>


                            <div
                                class="
                                    h-1.5
                                    overflow-hidden
                                    rounded-full
                                    bg-[#0D3025]
                                "
                            >

                                <div
                                    :class="[
                                        'stat-bar h-full rounded-full',
                                        currentStarter.accentBg
                                    ]"
                                    :style="{
                                        width:
                                            `${currentStarter.stats.defense}%`
                                    }"
                                ></div>

                            </div>

                        </div>



                        <!-- SPEED -->

                        <div>

                            <div
                                class="
                                    mb-2
                                    flex
                                    justify-between
                                    text-xs
                                "
                            >

                                <span class="text-white/60">
                                    Speed
                                </span>

                                <span class="font-bold text-white/70">
                                    {{ currentStarter.stats.speed }}
                                </span>

                            </div>


                            <div
                                class="
                                    h-1.5
                                    overflow-hidden
                                    rounded-full
                                    bg-[#0D3025]
                                "
                            >

                                <div
                                    :class="[
                                        'stat-bar h-full rounded-full',
                                        currentStarter.accentBg
                                    ]"
                                    :style="{
                                        width:
                                            `${currentStarter.stats.speed}%`
                                    }"
                                ></div>

                            </div>

                        </div>

                    </div>

                </Transition>



                <!-- ================================================== -->
                <!-- CHOOSE BUTTON -->
                <!-- ================================================== -->

                <button
                    :class="[
                        'group mt-auto flex w-full items-center justify-center gap-3 rounded-xl px-6 py-4 text-sm font-black text-[#02120C] transition-all duration-300 hover:-translate-y-1 hover:brightness-110',
                        currentStarter.accentBg,
                        currentStarter.accentGlow
                    ]"
                >

                    <span>
                        Choose
                    </span>

                    {{ currentStarter.name }}

                    <span
                        class="
                            transition-transform
                            duration-300
                            group-hover:translate-x-1
                        "
                    >
                        →
                    </span>

                </button>

            </div>



            <!-- ================================================== -->
            <!-- RIGHT VISUAL STAGE -->
            <!-- ================================================== -->

            <div
                class="
                    relative
                    min-h-[620px]
                    overflow-hidden
                    rounded-[22px]
                    border
                    border-[#164638]
                    bg-[#08231B]
                    shadow-[0_20px_60px_rgba(0,0,0,0.15)]
                "
            >

                <!-- TOP ACCENT -->

                <div
                    class="
                        absolute
                        left-0
                        right-0
                        top-0
                        z-50
                        h-px
                        bg-emerald-400/30
                    "
                ></div>


                <!-- ================================================== -->
                <!-- BIG GLOW -->
                <!-- ================================================== -->

                <div
                    :class="[
                        'absolute bottom-[145px] left-1/2 z-5 h-10 w-[60%] -translate-x-1/2 rounded-[50%] border transition-all duration-700',

                        currentStarter.accent === 'emerald'
                            ? 'border-emerald-400/30 bg-emerald-400/5 shadow-[0_0_70px_rgba(16,185,129,.18)]'
                            : '',

                        currentStarter.accent === 'orange'
                            ? 'border-orange-400/30 bg-orange-400/5 shadow-[0_0_70px_rgba(249,115,22,.18)]'
                            : '',

                        currentStarter.accent === 'cyan'
                            ? 'border-cyan-400/30 bg-cyan-400/5 shadow-[0_0_70px_rgba(6,182,212,.18)]'
                            : ''
                    ]"
                ></div>



                <!-- ================================================== -->
                <!-- RINGS -->
                <!-- ================================================== -->

                <div
                    :class="[
                        'absolute left-1/2 top-[42%] h-[430px] w-[430px] -translate-x-1/2 -translate-y-1/2 rounded-full border transition-all duration-700',

                        currentStarter.accent === 'emerald'
                            ? 'border-emerald-400/10'
                            : '',

                        currentStarter.accent === 'orange'
                            ? 'border-orange-400/10'
                            : '',

                        currentStarter.accent === 'cyan'
                            ? 'border-cyan-400/10'
                            : ''
                    ]"
                ></div>


                <div
                    :class="[
                        'absolute left-1/2 top-[42%] h-[310px] w-[310px] -translate-x-1/2 -translate-y-1/2 rounded-full border transition-all duration-700',

                        currentStarter.accent === 'emerald'
                            ? 'border-emerald-400/10'
                            : '',

                        currentStarter.accent === 'orange'
                            ? 'border-orange-400/10'
                            : '',

                        currentStarter.accent === 'cyan'
                            ? 'border-cyan-400/10'
                            : ''
                    ]"
                ></div>



                <!-- ================================================== -->
                <!-- DEX NUMBER -->
                <!-- ================================================== -->

                <div
                    class="
                        absolute
                        left-7
                        top-7
                        z-30
                    "
                >

                    <p
                        class="
                            text-[10px]
                            font-bold
                            uppercase
                            tracking-[0.3em]
                            text-white/25
                        "
                    >
                        Starter Dex
                    </p>


                    <p
                        :class="[
                            'mt-1 text-2xl font-black',
                            currentStarter.accentText
                        ]"
                    >
                        {{ currentStarter.dex }}
                    </p>

                </div>



                <!-- ================================================== -->
                <!-- 3D MODEL -->
                <!-- ================================================== -->

                <div
                    class="
                        absolute
                        inset-x-0
                        top-12
                        bottom-36
                        z-10
                    "
                >

                    <Transition
                        name="pokemon"
                        mode="out-in"
                    >

                        <div
                            :key="currentStarter.id"
                            class="
                                h-full
                                w-full
                            "
                        >

                            <Pokemon3D
                                :key="currentStarter.model"
                                :model-path="currentStarter.model"
                                :scale="currentStarter.modelScale"
                                :animate="currentStarter.animate"
                                :auto-rotate="currentStarter.autoRotate"
                                :rotation-speed="0.0015"
                                class="h-full w-full"
                            />

                        </div>

                    </Transition>

                </div>



                <!-- ================================================== -->
                <!-- PLATFORM -->
                <!-- ================================================== -->

                <div
                    :class="[
                        'absolute bottom-[145px] left-1/2 z-20 h-10 w-[60%] -translate-x-1/2 rounded-[50%] border-2 transition-all duration-700',

                        currentStarter.accent === 'emerald'
                            ? 'border-emerald-400/30 bg-emerald-400/5 shadow-[0_0_70px_rgba(16,185,129,.2)]'
                            : '',

                        currentStarter.accent === 'orange'
                            ? 'border-orange-400/30 bg-orange-400/5 shadow-[0_0_70px_rgba(249,115,22,.2)]'
                            : '',

                        currentStarter.accent === 'cyan'
                            ? 'border-cyan-400/30 bg-cyan-400/5 shadow-[0_0_70px_rgba(6,182,212,.2)]'
                            : ''
                    ]"
                >

                    <div
                        class="
                            absolute
                            inset-2
                            rounded-[50%]
                            border
                            border-white/5
                        "
                    ></div>

                </div>



                <!-- ================================================== -->
                <!-- PREVIOUS BUTTON -->
                <!-- ================================================== -->

                <button
                    @click="previousStarter"
                    :disabled="isChanging"
                    aria-label="Previous starter"
                    class="
                        group
                        absolute
                        left-5
                        top-1/2
                        z-40
                        flex
                        h-11
                        w-11
                        -translate-y-1/2
                        items-center
                        justify-center
                        rounded-xl
                        border
                        border-[#1A493B]
                        bg-[#0B2B21]
                        text-xl
                        text-white/60
                        transition-all
                        duration-300
                        hover:scale-105
                        hover:border-emerald-400/40
                        hover:bg-emerald-500
                        hover:text-black
                        disabled:opacity-30
                    "
                >

                    <span
                        class="
                            transition-transform
                            duration-300
                            group-hover:-translate-x-1
                        "
                    >
                        ←
                    </span>

                </button>



                <!-- ================================================== -->
                <!-- NEXT BUTTON -->
                <!-- ================================================== -->

                <button
                    @click="nextStarter"
                    :disabled="isChanging"
                    aria-label="Next starter"
                    class="
                        group
                        absolute
                        right-5
                        top-1/2
                        z-40
                        flex
                        h-11
                        w-11
                        -translate-y-1/2
                        items-center
                        justify-center
                        rounded-xl
                        border
                        border-[#1A493B]
                        bg-[#0B2B21]
                        text-xl
                        text-white/60
                        transition-all
                        duration-300
                        hover:scale-105
                        hover:border-emerald-400/40
                        hover:bg-emerald-500
                        hover:text-black
                        disabled:opacity-30
                    "
                >

                    <span
                        class="
                            transition-transform
                            duration-300
                            group-hover:translate-x-1
                        "
                    >
                        →
                    </span>

                </button>



                <!-- ================================================== -->
                <!-- BOTTOM CAROUSEL -->
                <!-- ================================================== -->

                <div
                    class="
                        absolute
                        bottom-5
                        left-1/2
                        z-40
                        flex
                        w-[90%]
                        -translate-x-1/2
                        flex-col
                        items-center
                        gap-4
                    "
                >

                    <!-- DOTS -->

                    <div
                        class="
                            flex
                            items-center
                            gap-2
                        "
                    >

                        <button
                            v-for="(starter, index) in starters"
                            :key="starter.id"
                            @click="changeStarter(index)"
                            :aria-label="`Select ${starter.name}`"
                            :class="[
                                'transition-all duration-500',

                                index === currentIndex
                                    ? `h-2.5 w-10 rounded-full ${starter.accentBg}`
                                    : 'h-2.5 w-2.5 rounded-full bg-white/20 hover:bg-white/40'
                            ]"
                        ></button>

                    </div>



                    <!-- STARTER NAMES -->

                    <div
                        class="
                            grid
                            w-full
                            max-w-lg
                            grid-cols-3
                            gap-2
                        "
                    >

                        <button
                            v-for="(starter, index) in starters"
                            :key="`${starter.id}-button`"
                            @click="changeStarter(index)"
                            :class="[
                                'rounded-xl border px-3 py-3 text-center transition-all duration-300',

                                index === currentIndex
                                    ? `${starter.accentBorder} bg-[#0D3025]`
                                    : 'border-[#123C30] bg-[#071C16]/60 hover:border-[#1A493B] hover:bg-[#0B2B21]'
                            ]"
                        >

                            <span
                                :class="[
                                    'block text-[9px] font-bold tracking-widest',

                                    index === currentIndex
                                        ? starter.accentText
                                        : 'text-white/25'
                                ]"
                            >
                                {{ starter.dex }}
                            </span>


                            <span
                                :class="[
                                    'mt-1 block text-[10px] font-black',

                                    index === currentIndex
                                        ? 'text-white'
                                        : 'text-white/40'
                                ]"
                            >
                                {{ starter.name }}
                            </span>

                        </button>

                    </div>

                </div>

            </div>

        </div>



        <!-- ================================================== -->
        <!-- BOTTOM FEATURES -->
        <!-- ================================================== -->

        <div
            class="
                mt-5
                grid
                gap-3
                sm:grid-cols-3
            "
        >

            <div
                class="
                    rounded-xl
                    border
                    border-[#123C30]
                    bg-[#071C16]
                    p-5
                "
            >

                <p
                    class="
                        mb-2
                        text-xs
                        font-black
                        uppercase
                        tracking-widest
                        text-emerald-400
                    "
                >
                    01 — Choose
                </p>


                <p
                    class="
                        text-sm
                        leading-6
                        text-white/40
                    "
                >
                    Choose the partner that matches
                    your playstyle.
                </p>

            </div>



            <div
                class="
                    rounded-xl
                    border
                    border-[#123C30]
                    bg-[#071C16]
                    p-5
                "
            >

                <p
                    class="
                        mb-2
                        text-xs
                        font-black
                        uppercase
                        tracking-widest
                        text-emerald-400
                    "
                >
                    02 — Train
                </p>


                <p
                    class="
                        text-sm
                        leading-6
                        text-white/40
                    "
                >
                    Train your partner and discover
                    its potential.
                </p>

            </div>



            <div
                class="
                    rounded-xl
                    border
                    border-[#123C30]
                    bg-[#071C16]
                    p-5
                "
            >

                <p
                    class="
                        mb-2
                        text-xs
                        font-black
                        uppercase
                        tracking-widest
                        text-emerald-400
                    "
                >
                    03 — Adventure
                </p>


                <p
                    class="
                        text-sm
                        leading-6
                        text-white/40
                    "
                >
                    Begin your journey and create
                    your own story.
                </p>

            </div>

        </div>

    </div>

</section>

</template>


<style scoped>

/* ======================================================
   POKEMON TRANSITION
   ====================================================== */

.pokemon-enter-active,
.pokemon-leave-active {

    transition:
        opacity 0.5s cubic-bezier(0.22, 1, 0.36, 1),
        transform 0.5s cubic-bezier(0.22, 1, 0.36, 1);

}


.pokemon-enter-from {

    opacity: 0;

    transform:
        translateX(50px)
        scale(0.92);

}


.pokemon-leave-to {

    opacity: 0;

    transform:
        translateX(-50px)
        scale(0.97);

}


/* ======================================================
   CONTENT TRANSITION
   ====================================================== */

.content-enter-active,
.content-leave-active {

    transition:
        opacity 0.3s ease,
        transform 0.3s ease;

}


.content-enter-from {

    opacity: 0;

    transform:
        translateY(10px);

}


.content-leave-to {

    opacity: 0;

    transform:
        translateY(-10px);

}


/* ======================================================
   STAT BAR
   ====================================================== */

.stat-bar {

    transition:
        width
        0.7s
        cubic-bezier(0.22, 1, 0.36, 1);

}


/* ======================================================
   REDUCED MOTION
   ====================================================== */

@media (
    prefers-reduced-motion: reduce
) {

    .pokemon-enter-active,
    .pokemon-leave-active,
    .content-enter-active,
    .content-leave-active {

        transition: none;

    }

}

</style>