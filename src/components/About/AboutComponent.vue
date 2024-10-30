<template>
    <div id="about" class="about-container">
        <div class="about-card" id="about-card">
            <canvas id="canvas"></canvas>
            <div class="about-content">
                <div class="about-content-inner">
                    <div class="about-text-container">
                        <div class="about-title">
                            About me
                        </div>
                        <p class="about-text">
                            I am Soraia, better known in internet as 0x4571! I am a 18 year old self-taught programmer, animator, artist and others, who is skilled both in front-end and back-end development. I started coding in 2018, making small and simple Roblox games. Since then, I have been learning with the best and have taken my skills a step further by learning how to animate Rigs (R6 and R15) on Roblox and by refining and learning new skills in the field of Computer Science. <br><br>In my free time, I like chatting with friends about philosophy, solving puzzles, or just going out for a walk. Whatever it is that you need done, I'll be here to work with you and to help you achieve your dreams!
                        </p>
                        <button class="like">
                            <span>
                                👍
                            </span>
                            <span>
                                {{ count }}
                            </span>
                        </button>
                    </div>
                </div>
                <div class="about-content-inner">
                    <img id="yo" src="../../assets/yo.png">
                </div>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import cssParticles from 'css-particles'
import axios from 'axios';

export default defineComponent({
    name: 'AboutComponent',
    data() {
        return {
            count: 1
        }
    },
    methods: {
        moveImage() {
            const height = document.body.clientHeight / 2
            const group = document.getElementById('yo') as HTMLElement
            document.addEventListener('mousemove', (e: MouseEvent) => {
                const degrees = (height - e.clientY) * 5 / height
                group.style.transform = `rotate(${degrees}deg)`
            })
        },
        async getCount() {
            console.log('akhsd')
            const data = await axios.get('https://api.countapi.xyz/get/aneksportfolio/likes')
            console.log('akjshd0', data)
        }
    },
    mounted() {
        this.moveImage()

        const card = document.getElementById('about-card') as HTMLElement
        const canvas = document.getElementById('canvas') as HTMLCanvasElement

        canvas.height = card.clientHeight
        canvas.width = card.clientWidth

        const system = new cssParticles.ParticleSystem(canvas, { x: canvas.width, y: canvas.height })
        console.log(system)
        system.ammount = 100
        system.speed = { x: { min: -5, max: 5 }, y: { min: -5, max: 5 } }
        system.diameter = { min: 1, max: 4 },
        system.life = { min: 5, max: 15 }
        system.init()

        this.getCount()
    }
})
</script>

<style scoped>
@import url("./styles.css");
</style>
