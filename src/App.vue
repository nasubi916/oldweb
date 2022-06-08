<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import nasubi from './components/nasubi.vue'
import test from './components/test.vue'
import pinia from './components/pinia.vue'

</script>

<template>
    <img alt="Vue logo" src="./assets/logo.png" /><br>
    <pinia/>
    <test />
    <nasubi />
</template>

<style>
#app {
    font-family: 'UDEV Gothic', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #fafafa;
    margin-top: 60px;
}
</style>