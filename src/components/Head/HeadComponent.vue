<template>
    <div class="head-container">
        <div class="header">
            <div class="title">
                Yo! 
                <span class="title-small">I'm</span>
                Soraia Santos
                <br>
                <span class="title-small">
                    a.k.a.
                </span>
                <span class="aneks">
                    0x4571  Vesp_Ithon  Sol  
                </span>
                <br>
            </div>
            <span class="subtitle">
                Independent Game Developer
            </span>
        </div>
        <a class="arrow" href="#about">
            <img src="../../assets/caret-down.svg">
        </a>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'HeadComponent'
})
</script>

<style scoped>
@import url("./styles.css");
</style>
