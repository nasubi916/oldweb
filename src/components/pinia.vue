<script setup lang="ts">
import { useCounterStore } from '../stores/counter';

const store = useCounterStore();
store.count++;
store.increment(2);

</script>

<template>
    <h1>Count is {{ store.count }}</h1>
    <h2>Double is {{ store.doubleCount }}</h2>
    <button @click="store.increment(1)">Increment</button>
    <button @click="store.waitAndAdd">Wait + Increment</button>
    <br>

</template>

<style>

</style>