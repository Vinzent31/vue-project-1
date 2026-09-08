<template>

<section
    id="gameplay"
    class="
        relative
        overflow-hidden
        bg-transparent
        py-24
        text-white
    "
>

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
            lg:px-10
        "
    >

        <!-- ================================================== -->
        <!-- HEADER -->
        <!-- ================================================== -->

        <div
            class="
                mb-12
                flex
                flex-col
                justify-between
                gap-6
                lg:flex-row
                lg:items-end
            "
        >

            <div class="max-w-2xl">

                <!-- SMALL LABEL -->

                <div
                    class="
                        mb-4
                        flex
                        items-center
                        gap-3
                        text-xs
                        font-black
                        uppercase
                        tracking-[0.25em]
                        text-emerald-400
                    "
                >

                    <span
                        class="
                            h-2
                            w-2
                            rounded-full
                            bg-emerald-400
                            shadow-[0_0_12px_rgba(52,211,153,0.6)]
                        "
                    ></span>

                    Gameplay Showcase

                </div>


                <!-- TITLE -->

                <h2
                    class="
                        text-4xl
                        font-black
                        leading-[1.05]
                        tracking-tight
                        sm:text-5xl
                        lg:text-6xl
                    "
                >

                    See the adventure

                    <span class="text-emerald-400">
                        in action.
                    </span>

                </h2>


                <!-- DESCRIPTION -->

                <p
                    class="
                        mt-5
                        max-w-xl
                        text-sm
                        leading-7
                        text-white/45
                        sm:text-base
                    "
                >

                    Explore the world, discover new Pokémon,
                    and experience your journey as a trainer
                    through the gameplay.

                </p>

            </div>


            <!-- VERSION -->

            <div
                class="
                    flex
                    items-center
                    gap-3
                    text-xs
                    font-bold
                    uppercase
                    tracking-widest
                    text-white/30
                "
            >

                <span>
                    Gameplay
                </span>

                <span
                    class="
                        h-px
                        w-10
                        bg-[#245449]
                    "
                ></span>

                <span class="text-emerald-400/70">
                    01
                </span>

            </div>

        </div>



        <!-- ================================================== -->
        <!-- GAMEPLAY LAYOUT -->
        <!-- ================================================== -->

        <div
            class="
                grid
                gap-5
                lg:grid-cols-[minmax(0,1fr)_320px]
            "
        >


            <!-- ================================================== -->
            <!-- VIDEO CARD -->
            <!-- ================================================== -->

            <div
                class="
                    group
                    relative
                    overflow-hidden
                    rounded-[22px]
                    border
                    border-[#245449]
                    bg-[#0B2420]
                    shadow-[0_25px_70px_rgba(0,0,0,0.22)]
                "
            >

                <!-- TOP ACCENT -->

                <div
                    class="
                        absolute
                        left-0
                        right-0
                        top-0
                        z-20
                        h-px
                        bg-emerald-400/50
                    "
                ></div>


                <!-- ================================================== -->
                <!-- VIDEO -->
                <!-- ================================================== -->

                <div
                    class="
                        relative
                        aspect-video
                        overflow-hidden
                        bg-black
                    "
                >

                    <video
                        class="
                            h-full
                            w-full
                            object-cover
                            transition-transform
                            duration-700
                            group-hover:scale-[1.015]
                        "
                        controls
                        preload="metadata"
                        poster=""
                    >

                        <source
                            src="/src/assets/images/Pokémon_ Let’s Go, Pikachu! and Pokémon_ Let’s Go, Eevee! - Overview Trailer - Nintendo Switch.mp4"
                            type="video/mp4"
                        />

                        Browser kamu tidak mendukung
                        video playback.

                    </video>


                    <!-- ================================================== -->
                    <!-- VIDEO LABEL -->
                    <!-- ================================================== -->

                    <div
                        class="
                            pointer-events-none
                            absolute
                            left-5
                            top-5
                            z-10
                            flex
                            items-center
                            gap-2
                            rounded-lg
                            border
                            border-white/10
                            bg-black/40
                            px-3
                            py-2
                            text-[10px]
                            font-bold
                            uppercase
                            tracking-widest
                            text-white/70
                            backdrop-blur-sm
                        "
                    >

                        <span
                            class="
                                h-1.5
                                w-1.5
                                rounded-full
                                bg-emerald-400
                            "
                        ></span>

                        Live Gameplay

                    </div>


                    <!-- ================================================== -->
                    <!-- VIDEO INDEX -->
                    <!-- ================================================== -->

                    <div
                        class="
                            pointer-events-none
                            absolute
                            bottom-5
                            right-5
                            z-10
                            text-[10px]
                            font-black
                            tracking-[0.25em]
                            text-white/40
                        "
                    >

                        GAMEPLAY // 01

                    </div>

                </div>



                <!-- ================================================== -->
                <!-- VIDEO FOOTER -->
                <!-- ================================================== -->

                <div
                    class="
                        flex
                        flex-col
                        gap-4
                        border-t
                        border-[#245449]
                        bg-[#102A25]
                        p-5
                        sm:flex-row
                        sm:items-center
                        sm:justify-between
                    "
                >

                    <div>

                        <p
                            class="
                                text-sm
                                font-black
                                text-[#F1F7F4]
                            "
                        >

                            A New Journey Begins

                        </p>


                        <p
                            class="
                                mt-1
                                text-xs
                                text-[#8DA39C]
                            "
                        >

                            Explore the world and become
                            the next Pokémon Trainer.

                        </p>

                    </div>


                    <div
                        class="
                            flex
                            items-center
                            gap-2
                            text-[10px]
                            font-bold
                            uppercase
                            tracking-widest
                            text-[#607A72]
                        "
                    >

                        <span
                            class="
                                h-1.5
                                w-1.5
                                rounded-full
                                bg-emerald-400
                            "
                        ></span>

                        1080p

                    </div>

                </div>

            </div>



            <!-- ================================================== -->
            <!-- JOURNEY LOG CARD -->
            <!-- ================================================== -->

            <div
                class="
                    flex
                    flex-col
                    rounded-[22px]
                    border
                    border-[#245449]
                    bg-[#102A25]
                    p-6
                    shadow-[0_20px_60px_rgba(0,0,0,0.22)]
                "
            >


                <!-- ================================================== -->
                <!-- PANEL HEADER -->
                <!-- ================================================== -->

                <div
                    class="
                        mb-8
                        flex
                        items-start
                        justify-between
                    "
                >

                    <div>

                        <p
                            class="
                                text-[10px]
                                font-bold
                                uppercase
                                tracking-[0.28em]
                                text-[#7F9991]
                            "
                        >

                            Journey Log

                        </p>


                        <h3
                            class="
                                mt-2
                                text-xl
                                font-black
                                tracking-tight
                                text-[#F1F7F4]
                            "
                        >

                            Explore

                        </h3>

                    </div>


                    <!-- ICON -->

                    <div
                        class="
                            flex
                            h-9
                            w-9
                            items-center
                            justify-center
                            rounded-lg
                            border
                            border-[#286052]
                            bg-[#173831]
                            text-emerald-400
                        "
                    >

                        <span class="text-sm">
                            ✦
                        </span>

                    </div>

                </div>



                <!-- ================================================== -->
                <!-- FEATURE 01 -->
                <!-- ================================================== -->

                <div
                    class="
                        border-b
                        border-[#1C443A]
                        pb-6
                    "
                >

                    <div
                        class="
                            mb-4
                            flex
                            items-center
                            justify-between
                        "
                    >

                        <span
                            class="
                                text-[10px]
                                font-black
                                tracking-widest
                                text-[#00D6A0]
                            "
                        >

                            01

                        </span>


                        <span
                            class="
                                text-[9px]
                                font-bold
                                uppercase
                                tracking-widest
                                text-[#607A72]
                            "
                        >

                            Explore

                        </span>

                    </div>


                    <h4
                        class="
                            text-sm
                            font-black
                            text-[#F1F7F4]
                        "
                    >

                        Discover the World

                    </h4>


                    <p
                        class="
                            mt-3
                            text-xs
                            leading-6
                            text-[#8DA39C]
                        "
                    >

                        Travel through different areas,
                        discover hidden locations, and encounter
                        new adventures.

                    </p>

                </div>



                <!-- ================================================== -->
                <!-- FEATURE 02 -->
                <!-- ================================================== -->

                <div
                    class="
                        border-b
                        border-[#1C443A]
                        py-6
                    "
                >

                    <div
                        class="
                            mb-4
                            flex
                            items-center
                            justify-between
                        "
                    >

                        <span
                            class="
                                text-[10px]
                                font-black
                                tracking-widest
                                text-[#00D6A0]
                            "
                        >

                            02

                        </span>


                        <span
                            class="
                                text-[9px]
                                font-bold
                                uppercase
                                tracking-widest
                                text-[#607A72]
                            "
                        >

                            Battle

                        </span>

                    </div>


                    <h4
                        class="
                            text-sm
                            font-black
                            text-[#F1F7F4]
                        "
                    >

                        Train Your Partner

                    </h4>


                    <p
                        class="
                            mt-3
                            text-xs
                            leading-6
                            text-[#8DA39C]
                        "
                    >

                        Build your team, train your Pokémon,
                        and prepare for battle.

                    </p>

                </div>



                <!-- ================================================== -->
                <!-- FEATURE 03 -->
                <!-- ================================================== -->

                <div
                    class="
                        py-6
                    "
                >

                    <div
                        class="
                            mb-4
                            flex
                            items-center
                            justify-between
                        "
                    >

                        <span
                            class="
                                text-[10px]
                                font-black
                                tracking-widest
                                text-[#00D6A0]
                            "
                        >

                            03

                        </span>


                        <span
                            class="
                                text-[9px]
                                font-bold
                                uppercase
                                tracking-widest
                                text-[#607A72]
                            "
                        >

                            Story

                        </span>

                    </div>


                    <h4
                        class="
                            text-sm
                            font-black
                            text-[#F1F7F4]
                        "
                    >

                        Create Your Story

                    </h4>


                    <p
                        class="
                            mt-3
                            text-xs
                            leading-6
                            text-[#8DA39C]
                        "
                    >

                        Every trainer has a different journey.
                        What will yours become?

                    </p>

                </div>



                <!-- ================================================== -->
                <!-- CTA -->
                <!-- ================================================== -->

                <button
                    class="
                        mt-auto
                        flex
                        w-full
                        items-center
                        justify-center
                        gap-3
                        rounded-xl
                        bg-[#00D6A0]
                        px-5
                        py-3.5
                        text-xs
                        font-black
                        uppercase
                        tracking-wider
                        text-[#031812]
                        transition-all
                        duration-300
                        hover:-translate-y-0.5
                        hover:bg-[#22E0AE]
                        hover:shadow-[0_10px_30px_rgba(0,214,160,0.18)]
                    "
                >

                    Explore the World

                    <span>
                        →
                    </span>

                </button>

            </div>

        </div>



        <!-- ================================================== -->
        <!-- BOTTOM STATS -->
        <!-- ================================================== -->

        <div
            class="
                mt-5
                grid
                grid-cols-2
                gap-3
                md:grid-cols-4
            "
        >


            <!-- WORLD -->

            <div
                class="
                    rounded-xl
                    border
                    border-[#245449]
                    bg-[#102A25]
                    p-4
                    transition-colors
                    duration-300
                    hover:border-[#286052]
                "
            >

                <p
                    class="
                        text-[9px]
                        font-bold
                        uppercase
                        tracking-widest
                        text-[#607A72]
                    "
                >

                    World

                </p>


                <p
                    class="
                        mt-2
                        text-sm
                        font-black
                        text-[#00D6A0]
                    "
                >

                    Explore

                </p>

            </div>



            <!-- BATTLES -->

            <div
                class="
                    rounded-xl
                    border
                    border-[#245449]
                    bg-[#102A25]
                    p-4
                    transition-colors
                    duration-300
                    hover:border-[#286052]
                "
            >

                <p
                    class="
                        text-[9px]
                        font-bold
                        uppercase
                        tracking-widest
                        text-[#607A72]
                    "
                >

                    Battles

                </p>


                <p
                    class="
                        mt-2
                        text-sm
                        font-black
                        text-[#00D6A0]
                    "
                >

                    Strategic

                </p>

            </div>



            <!-- ADVENTURE -->

            <div
                class="
                    rounded-xl
                    border
                    border-[#245449]
                    bg-[#102A25]
                    p-4
                    transition-colors
                    duration-300
                    hover:border-[#286052]
                "
            >

                <p
                    class="
                        text-[9px]
                        font-bold
                        uppercase
                        tracking-widest
                        text-[#607A72]
                    "
                >

                    Adventure

                </p>


                <p
                    class="
                        mt-2
                        text-sm
                        font-black
                        text-[#00D6A0]
                    "
                >

                    Endless

                </p>

            </div>



            <!-- JOURNEY -->

            <div
                class="
                    rounded-xl
                    border
                    border-[#245449]
                    bg-[#102A25]
                    p-4
                    transition-colors
                    duration-300
                    hover:border-[#286052]
                "
            >

                <p
                    class="
                        text-[9px]
                        font-bold
                        uppercase
                        tracking-widest
                        text-[#607A72]
                    "
                >

                    Journey

                </p>


                <p
                    class="
                        mt-2
                        text-sm
                        font-black
                        text-[#00D6A0]
                    "
                >

                    Yours

                </p>

            </div>

        </div>

    </div>

</section>
</template>