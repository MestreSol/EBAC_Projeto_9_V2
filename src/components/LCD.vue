<script setup lang="ts">
import { defineProps } from 'vue';

const props = defineProps({
  display: {
    type: Array,
    required: true
  }
});
</script>

<template>
    <div class="lcd">
        <div class="scrollable">
            <div v-for="(line, index) in display" :key="index">{{ line }}</div>
        </div>
    </div>
</template>

<style scoped>
.lcd {
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #f2f2f2;
    border: 1px solid #ccc;
    border-radius: 10px;
    width: 250px;
    height: 100px;
    margin: 0 auto;
    width: 100%;
    height: 100%;
    overflow: hidden;
}

h1{
    font-weight: 200;
    font-size: 2.2ch;
    position: relative;
    top: -10px;
    font-family: "Silkscreen", sans-serif;

}

.scrollable {
    max-height: 100px; /* Ajuste conforme necessário */
    overflow-y: auto;
    font-weight: 200;
    font-size: 2.2ch;
    position: relative;
    top: -10px;
    font-family: "Silkscreen", sans-serif;
    color: #000;
}
</style>