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

    <p>{{ number }}</p>
</template>

<script lang="ts">
// こっちは初期設定以外を置くと良い(処理順が遅い)
const number=ref(0);
</script>

<style>
.root {
    position: relative;
    /* これがあるとこの要素から数えて位置が決まる */
}
</style>

<style scoped>
/* このコンポーネントにしか反映されない */
</style>