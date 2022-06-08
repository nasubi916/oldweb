<script setup lang="ts">
import { ref } from "vue";

const useUser = () => {
    const name = ref("おまえは");

    const changeName = () => {
        name.value = "gorilla";
    };

    return ({
        name,
        changeName,
    });
}

const { name, changeName } = (useUser());

console.log(name.value);
</script>

<template>
    -------------------------------------
    <br>
    <button @click="changeName">{{ name }}</button>
</template>

<style>
.root {
    position: relative;
    /* これがあるとこの要素から数えて位置が決まる */
}
</style>