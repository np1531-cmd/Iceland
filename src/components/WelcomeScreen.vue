<script setup lang="ts">
import { ref, onMounted, onUnmounted} from 'vue';

const layer = ref<null | HTMLElement>(null)

const movePlane = () => {
    const scrollY = window.scrollY

    if (layer.value) {
        layer.value.style.left = `${scrollY}px`
    }
}

onMounted(() => {
    window.addEventListener('scroll', movePlane)
})

onUnmounted(() => {
    window.removeEventListener('scroll', movePlane)
})

</script>

<template>
    <div class="root">
        <div ref="layer" class="layer">
            <div class="texts">
                <div class="title">
                    Начните путешествие в
                    <div class="content">
                        <span class="accent accent-stroke">Исландию</span><br>
                        <span class="accent accent-wave">Исландию</span><br>
                        </div>
                    прямо сейчас
                </div>
            </div>
            <img src="/images/plane-min.png" alt="Plane" class="plane">
        </div>
        <div class="bg bg-1"></div>
            <div class="welcome-block">
                <div class="welcome-text">
                    Welcome to
                    <div class="transparent-text">
                        Iceland
                    </div>
                </div>
            </div>
        <div class="bg bg-2"></div>
    </div>
</template>

<style lang="sass" scoped>
@use '../assets/styles/variables'

@keyframes wave
    0%, 100%
        clip-path: polygon(0% 39%, 9% 41%, 18% 45%, 24% 50%, 31% 55%, 39% 60%, 46% 62%, 53% 62%, 62% 59%, 68% 54%, 76% 50%, 83% 49%, 90% 50%, 97% 52%, 100% 54%, 100% 100%, 0% 100%)
    50%
        clip-path: polygon(0 49%, 5% 53%, 11% 57%, 16% 59%, 28% 64%, 38% 57%, 41% 58%, 48% 56%, 54% 58%, 64% 62%, 71% 66%, 79% 68%, 86% 66%, 92% 64%, 100% 62%, 100% 100%, 0% 100%)

.root
    //font-family: "Poppins", sans-serif
    color: variables.$white
    background-color: variables.$backgroundColor

.layer
    position: fixed
    left: 0
    height: 100vh
    width: 100%
    background-color: variables.$backgroundColor

.texts
    position: absolute
    left: 50%
    top: 50%
    transform: translate(-50%, -50%)
    font-size: 44px
    font-weight: 700
    letter-spacing: .05em
    font-family: 'Roboto', sans-serif
    text-align: center

.plane
    height: 100vh
    position: absolute
    z-index: 2
    left: -50vh

.bg
    background-size: cover
    background-attachment: fixed

.bg-1
    background-image: url('/images/bg1-min.jpg')
    height: 240vh

.welcome-block
    height: 50vh
    display: flex
    justify-content: center
    align-items: center
    text-align: center

.welcome-text
    font-size: 3em
    font-weight: 200
    letter-spacing: .25em
    line-height: 2.5em
    color: #fff
    text-transform: uppercase

.transparent-text
    font-size: 4em
    font-weight: 900
    letter-spacing: 0
    background: url(../images/bg2-min.jpeg)
    background-size: cover
    background-attachment: fixed
    -webkit-background-clip: text
    color: transparent

.bg-2
    background-image: url('/images/bg2-min.jpeg')
    height: 130vh

.content
    position: relative

.accent
    position: absolute
    left: 50%
    top: 50%
    font-size: 120px
    transform: translate(-50%, -50%)
    color: transparent

.accent-stroke
    -webkit-text-stroke: 2px variables.$accentColor

.accent-wave
    color: variables.$accentColor
    animation: wave 4s ease-in-out infinite

</style>
