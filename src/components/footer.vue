<template>

<footer
    class="
        relative
        overflow-hidden
        bg-black
        pb-8
        pt-20
        text-white
    "
>

    <div
        class="
            mx-auto
            max-w-[1400px]
            px-6
            lg:px-10
        "
    >

        <!-- ================================================ -->
        <!-- FOOTER CARD -->
        <!-- ================================================ -->

        <div
            class="
                overflow-hidden
                rounded-[24px]
                border
                border-[#1C2D28]
                bg-[#050505]
            "
        >

            <!-- ============================================ -->
            <!-- MAIN -->
            <!-- ============================================ -->

            <div
                class="
                    grid
                    gap-12
                    p-7
                    sm:p-10
                    lg:grid-cols-[1.4fr_1fr_1fr]
                    lg:p-12
                "
            >

                <!-- ======================================== -->
                <!-- BRAND -->
                <!-- ======================================== -->

                <div>

                    <a
                        href="#"
                        class="
                            inline-flex
                            items-center
                            gap-3
                        "
                    >

                        <!-- LOGO -->

                        <div
                            class="
                                flex
                                h-11
                                w-11
                                items-center
                                justify-center
                                rounded-xl
                                border
                                border-[#1C3D34]
                                bg-[#0D211C]
                                text-emerald-400
                            "
                        >

                            <span
                                class="
                                    text-lg
                                    font-black
                                "
                            >
                                P
                            </span>

                        </div>


                        <!-- BRAND -->

                        <div>

                            <p
                                class="
                                    text-sm
                                    font-black
                                    tracking-tight
                                    text-white
                                "
                            >
                                POKÉMON
                            </p>

                            <p
                                class="
                                    text-[9px]
                                    font-bold
                                    uppercase
                                    tracking-[0.25em]
                                    text-white/30
                                "
                            >
                                Pokemon LeafGreen
                            </p>

                        </div>

                    </a>


                    <!-- DESCRIPTION -->

                    <p
                        class="
                            mt-6
                            max-w-sm
                            text-sm
                            leading-7
                            text-white/40
                        "
                    >
                        Every adventure begins with a choice.
                        Choose your partner, explore the world,
                        and create your own journey.
                    </p>


                    <!-- STATUS -->

                    <div
                        class="
                            mt-6
                            inline-flex
                            items-center
                            gap-2
                            rounded-full
                            border
                            border-[#1C3D34]
                            bg-[#0D211C]
                            px-3
                            py-2
                            text-[9px]
                            font-bold
                            uppercase
                            tracking-widest
                            text-white/40
                        "
                    >

                        <span
                            class="
                                h-1.5
                                w-1.5
                                rounded-full
                                bg-[#00D6A0]
                                shadow-[0_0_8px_rgba(0,214,160,0.5)]
                            "
                        ></span>

                        Adventure Awaits

                    </div>

                </div>



                <!-- ======================================== -->
                <!-- NAVIGATION -->
                <!-- ======================================== -->

                <div>

                    <p
                        class="
                            mb-5
                            text-[10px]
                            font-black
                            uppercase
                            tracking-[0.25em]
                            text-white/25
                        "
                    >
                        Explore
                    </p>


                    <nav
                        class="
                            flex
                            flex-col
                            items-start
                            gap-4
                        "
                    >

                        <a
                            href="#home"
                            class="
                                text-sm
                                text-white/45
                                transition-colors
                                duration-300
                                hover:text-[#00D6A0]
                            "
                        >
                            Home
                        </a>


                        <a
                            href="#starter"
                            class="
                                text-sm
                                text-white/45
                                transition-colors
                                duration-300
                                hover:text-[#00D6A0]
                            "
                        >
                            Starters
                        </a>


                        <a
                            href="#gameplay"
                            class="
                                text-sm
                                text-white/45
                                transition-colors
                                duration-300
                                hover:text-[#00D6A0]
                            "
                        >
                            Gameplay
                        </a>


                        <a
                            href="#about"
                            class="
                                text-sm
                                text-white/45
                                transition-colors
                                duration-300
                                hover:text-[#00D6A0]
                            "
                        >
                            About
                        </a>

                    </nav>

                </div>



                <!-- ======================================== -->
                <!-- CONNECT -->
                <!-- ======================================== -->

                <div>

                    <p
                        class="
                            mb-5
                            text-[10px]
                            font-black
                            uppercase
                            tracking-[0.25em]
                            text-white/25
                        "
                    >
                        Continue The Journey
                    </p>


                    <p
                        class="
                            max-w-xs
                            text-sm
                            leading-6
                            text-white/40
                        "
                    >
                        Stay connected and discover
                        more about the world.
                    </p>



                   

                </div>

            </div>



            <!-- ============================================ -->
            <!-- DIVIDER -->
            <!-- ============================================ -->

            <div
                class="
                    mx-7
                    h-px
                    bg-[#1C2D28]
                    sm:mx-10
                    lg:mx-12
                "
            ></div>



            <!-- ============================================ -->
            <!-- BOTTOM -->
            <!-- ============================================ -->

            <div
                class="
                    flex
                    flex-col
                    gap-4
                    px-7
                    py-6
                    sm:px-10
                    lg:flex-row
                    lg:items-center
                    lg:justify-between
                    lg:px-12
                "
            >

                <p
                    class="
                        text-[10px]
                        font-medium
                        tracking-wide
                        text-white/25
                    "
                >
                    © 2026 Pokemon Leafgreen
                    Built for adventure.
                </p>


                <div
                    class="
                        flex
                        items-center
                        gap-4
                        text-[9px]
                        font-bold
                        uppercase
                        tracking-widest
                        text-white/25
                    "
                >

                    <span>
                        Made with
                        <span class="text-[#00D6A0]">
                            ♥
                        </span>
                    </span>


                    <span
                        class="
                            h-1
                            w-1
                            rounded-full
                            bg-[#1C3D34]
                        "
                    ></span>


                    <span>
                        Kanto Region
                    </span>

                </div>

            </div>

        </div>



        <!-- ================================================ -->
        <!-- BOTTOM TEXT -->
        <!-- ================================================ -->

        <div
            class="
                flex
                items-center
                justify-center
                gap-3
                pt-6
            "
        >

            <span
                class="
                    h-px
                    w-8
                    bg-[#1C2D28]
                "
            ></span>


            <p
                class="
                    text-[8px]
                    font-bold
                    uppercase
                    tracking-[0.3em]
                    text-white/15
                "
            >
                Your adventure starts here
            </p>


            <span
                class="
                    h-px
                    w-8
                    bg-[#1C2D28]
                "
            ></span>

        </div>

    </div>

</footer>
</template>