<script setup>
import { ref, onMounted, onBeforeUnmount, watch } from 'vue'
import * as THREE from 'three'
import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader.js'
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls.js'


// ============================================================
// PROPS
// ============================================================

const props = defineProps({

    // Lokasi file .glb
    modelPath: {
        type: String,
        required: true
    },

    // Ukuran model
    scale: {
        type: Number,
        default: 1
    },

    // Idle animation dari file GLB
    animate: {
        type: Boolean,
        default: true
    },

    // Rotasi otomatis model
    autoRotate: {
        type: Boolean,
        default: true
    },

    // Kecepatan rotasi
    rotationSpeed: {
        type: Number,
        default: 0.0015
    }

})


// ============================================================
// CONTAINER
// ============================================================

const container = ref(null)


// ============================================================
// THREE.JS VARIABLES
// ============================================================

let scene = null
let camera = null
let renderer = null
let controls = null

let currentModel = null
let mixer = null

let animationFrame = null
let resizeObserver = null

const clock = new THREE.Clock()


// ============================================================
// INITIALIZE THREE.JS
// ============================================================

function initScene() {

    if (!container.value) return


    // ========================================================
    // SCENE
    // ========================================================

    scene = new THREE.Scene()

    // Background transparan
    scene.background = null


    // ========================================================
    // CAMERA
    // ========================================================

    camera = new THREE.PerspectiveCamera(
        35,
        1,
        0.01,
        1000
    )

    camera.position.set(
        0,
        0.5,
        5
    )


    // ========================================================
    // RENDERER
    // ========================================================

    renderer = new THREE.WebGLRenderer({
        antialias: true,
        alpha: true
    })

    renderer.setPixelRatio(
        Math.min(window.devicePixelRatio, 2)
    )

    renderer.setSize(
        container.value.clientWidth,
        container.value.clientHeight
    )

    renderer.outputColorSpace =
        THREE.SRGBColorSpace

    renderer.shadowMap.enabled = true

    renderer.shadowMap.type =
        THREE.PCFSoftShadowMap


    container.value.appendChild(
        renderer.domElement
    )


    // ========================================================
    // LIGHTING
    // ========================================================

    // Ambient light
    const ambientLight =
        new THREE.AmbientLight(
            0xffffff,
            2.5
        )

    scene.add(
        ambientLight
    )


    // Main light
    const keyLight =
        new THREE.DirectionalLight(
            0xffffff,
            3
        )

    keyLight.position.set(
        5,
        8,
        6
    )

    keyLight.castShadow = true

    scene.add(
        keyLight
    )


    // Green fill light
    const fillLight =
        new THREE.DirectionalLight(
            0x8affd8,
            1.5
        )

    fillLight.position.set(
        -5,
        4,
        5
    )

    scene.add(
        fillLight
    )


    // Rim light
    const rimLight =
        new THREE.DirectionalLight(
            0x42ffd1,
            1.5
        )

    rimLight.position.set(
        0,
        5,
        -6
    )

    scene.add(
        rimLight
    )


    // ========================================================
    // ORBIT CONTROLS
    // ========================================================

    controls = new OrbitControls(
        camera,
        renderer.domElement
    )

    // Smooth movement
    controls.enableDamping = true

    controls.dampingFactor = 0.08

    // Tidak bisa geser model
    controls.enablePan = false

    // Tidak bisa zoom
    controls.enableZoom = false

    // Kita menggunakan rotasi sendiri
    controls.autoRotate = false

    // Batasi rotasi vertikal
    controls.minPolarAngle =
        Math.PI * 0.35

    controls.maxPolarAngle =
        Math.PI * 0.65

    controls.target.set(
        0,
        0,
        0
    )


    // ========================================================
    // LOAD MODEL
    // ========================================================

    loadModel()


    // ========================================================
    // RESPONSIVE
    // ========================================================

    resizeObserver =
        new ResizeObserver(() => {

            resizeRenderer()

        })

    resizeObserver.observe(
        container.value
    )


    // ========================================================
    // ANIMATION LOOP
    // ========================================================

    animateLoop()

}


// ============================================================
// LOAD MODEL
// ============================================================

function loadModel() {

    if (!scene) return


    // ========================================================
    // REMOVE MODEL SEBELUMNYA
    // ========================================================

    if (currentModel) {

        scene.remove(
            currentModel
        )

        disposeModel(
            currentModel
        )

        currentModel = null

    }


    // Reset mixer
    mixer = null


    // ========================================================
    // GLTF LOADER
    // ========================================================

    const loader =
        new GLTFLoader()


    loader.load(

        props.modelPath,


        // ====================================================
        // SUCCESS
        // ====================================================

        (gltf) => {

            const model =
                gltf.scene


            currentModel =
                model


            // =================================================
            // SCALE MODEL
            // =================================================

            model.scale.setScalar(
                props.scale
            )


            // =================================================
            // SHADOW
            // =================================================

            model.traverse(
                (child) => {

                    if (child.isMesh) {

                        child.castShadow = true

                        child.receiveShadow = true

                    }

                }
            )


            // =================================================
            // BOUNDING BOX
            // =================================================

            const box =
                new THREE.Box3()
                    .setFromObject(model)


            const center =
                new THREE.Vector3()


            const size =
                new THREE.Vector3()


            box.getCenter(
                center
            )

            box.getSize(
                size
            )


            // =================================================
            // CENTER MODEL
            // =================================================

            model.position.x -=
                center.x

            model.position.z -=
                center.z


            // =================================================
            // MODEL DIMENSIONS
            // =================================================

            const width =
                Math.max(
                    size.x,
                    size.z
                )


            const height =
                size.y


            const maxDimension =
                Math.max(
                    width,
                    height
                )


            // =================================================
            // CAMERA FRAMING
            // =================================================

            const fov =
                camera.fov *
                Math.PI /
                180


            let distance =
                maxDimension /
                (
                    2 *
                    Math.tan(
                        fov / 2
                    )
                )


            // Extra space
            distance *= 1.35


            // =================================================
            // CAMERA POSITION
            // =================================================

            camera.position.set(
                0,
                height * 0.15,
                distance
            )


            // =================================================
            // CAMERA TARGET
            // =================================================

            controls.target.set(
                0,
                height * 0.30,
                0
            )


            camera.lookAt(
                controls.target
            )


            // =================================================
            // ADD MODEL
            // =================================================

            scene.add(
                model
            )


            // =================================================
            // IDLE ANIMATION
            // =================================================

            /*
             *
             * animate = true
             * ----------------
             * GLB animation dimainkan.
             *
             *
             * animate = false
             * -----------------
             * GLB animation TIDAK dimainkan.
             *
             */

            if (
                props.animate &&
                gltf.animations &&
                gltf.animations.length > 0
            ) {

                mixer =
                    new THREE.AnimationMixer(
                        model
                    )


                gltf.animations.forEach(
                    (clip) => {

                        const action =
                            mixer.clipAction(
                                clip
                            )

                        action.play()

                    }
                )

            }


            // =================================================
            // SMOOTH SCALE IN
            // =================================================

            const targetScale =
                props.scale


            model.scale.setScalar(
                0.01
            )


            let progress = 0


            function scaleIn() {

                if (
                    !currentModel ||
                    currentModel !== model
                ) {

                    return

                }


                progress += 0.08


                const clampedProgress =
                    Math.min(
                        progress,
                        1
                    )


                // Ease out
                const eased =
                    1 -
                    Math.pow(
                        1 -
                        clampedProgress,
                        3
                    )


                model.scale.setScalar(
                    targetScale *
                    eased
                )


                if (
                    progress < 1
                ) {

                    requestAnimationFrame(
                        scaleIn
                    )

                }

            }


            scaleIn()

        },


        // ====================================================
        // LOADING
        // ====================================================

        (xhr) => {

            if (xhr.total) {

                const percent =
                    (
                        xhr.loaded /
                        xhr.total
                    ) * 100


                console.log(
                    `Loading ${props.modelPath}: ${percent.toFixed(0)}%`
                )

            }

        },


        // ====================================================
        // ERROR
        // ====================================================

        (error) => {

            console.error(
                '❌ Failed to load GLB:',
                props.modelPath
            )

            console.error(
                error
            )

        }

    )

}


// ============================================================
// ANIMATION LOOP
// ============================================================

function animateLoop() {

    animationFrame =
        requestAnimationFrame(
            animateLoop
        )


    const delta =
        clock.getDelta()


    // ========================================================
    // GLB IDLE ANIMATION
    // ========================================================

    if (
        mixer &&
        props.animate
    ) {

        mixer.update(
            delta
        )

    }


    // ========================================================
    // AUTO ROTATE
    // ========================================================

    /*
     *
     * INI DIPISAH DARI IDLE ANIMATION.
     *
     * Jadi:
     *
     * animate = false
     * autoRotate = true
     *
     * hasilnya:
     *
     * idle animation OFF
     * auto rotation ON
     *
     */

    if (
        currentModel &&
        props.autoRotate
    ) {

        currentModel.rotation.y +=
            props.rotationSpeed

    }


    // ========================================================
    // CONTROLS
    // ========================================================

    if (controls) {

        controls.update()

    }


    // ========================================================
    // RENDER
    // ========================================================

    if (
        renderer &&
        scene &&
        camera
    ) {

        renderer.render(
            scene,
            camera
        )

    }

}


// ============================================================
// RESIZE
// ============================================================

function resizeRenderer() {

    if (
        !container.value ||
        !camera ||
        !renderer
    ) {

        return

    }


    const width =
        container.value.clientWidth


    const height =
        container.value.clientHeight


    if (
        width <= 0 ||
        height <= 0
    ) {

        return

    }


    camera.aspect =
        width / height


    camera.updateProjectionMatrix()


    renderer.setSize(
        width,
        height,
        false
    )

}


// ============================================================
// DISPOSE MODEL
// ============================================================

function disposeModel(model) {

    model.traverse(
        (child) => {

            // Geometry
            if (child.geometry) {

                child.geometry.dispose()

            }


            // Material
            if (child.material) {

                if (
                    Array.isArray(
                        child.material
                    )
                ) {

                    child.material.forEach(
                        (material) => {

                            disposeMaterial(
                                material
                            )

                        }
                    )

                } else {

                    disposeMaterial(
                        child.material
                    )

                }

            }

        }
    )

}


// ============================================================
// DISPOSE MATERIAL
// ============================================================

function disposeMaterial(
    material
) {

    for (
        const key in material
    ) {

        const value =
            material[key]


        if (
            value &&
            value.isTexture
        ) {

            value.dispose()

        }

    }


    material.dispose()

}


// ============================================================
// WATCH MODEL PATH
// ============================================================

watch(
    () => props.modelPath,

    () => {

        if (scene) {

            loadModel()

        }

    }
)


// ============================================================
// WATCH SCALE
// ============================================================

watch(
    () => props.scale,

    () => {

        if (scene) {

            loadModel()

        }

    }
)


// ============================================================
// WATCH ANIMATION
// ============================================================

watch(
    () => props.animate,

    (newValue) => {

        // ----------------------------------------------------
        // Animation dimatikan
        // ----------------------------------------------------

        if (!newValue) {

            if (mixer) {

                mixer.stopAllAction()

                mixer = null

            }

        }


        // ----------------------------------------------------
        // Animation dinyalakan
        // ----------------------------------------------------

        else {

            /*
             * Reload supaya animation
             * dari GLB dibuat kembali.
             */

            if (scene) {

                loadModel()

            }

        }

    }
)


// ============================================================
// WATCH AUTO ROTATE
// ============================================================

watch(
    () => props.autoRotate,

    (newValue) => {

        console.log(
            'Auto rotate:',
            newValue
        )

    }
)


// ============================================================
// MOUNT
// ============================================================

onMounted(() => {

    initScene()

})


// ============================================================
// UNMOUNT
// ============================================================

onBeforeUnmount(() => {

    // Stop animation frame
    if (animationFrame) {

        cancelAnimationFrame(
            animationFrame
        )

    }


    // Stop resize observer
    if (resizeObserver) {

        resizeObserver.disconnect()

    }


    // Dispose controls
    if (controls) {

        controls.dispose()

    }


    // Dispose model
    if (currentModel) {

        disposeModel(
            currentModel
        )

    }


    // Dispose renderer
    if (renderer) {

        renderer.dispose()

    }


    // Remove canvas
    if (
        renderer &&
        renderer.domElement &&
        renderer.domElement.parentNode
    ) {

        renderer.domElement.parentNode.removeChild(
            renderer.domElement
        )

    }


    // Reset variables
    scene = null
    camera = null
    renderer = null
    controls = null
    currentModel = null
    mixer = null

})

</script>


<template>

    <div
        ref="container"
        class="
            relative
            h-full
            w-full
            overflow-visible
        "
    ></div>

</template>