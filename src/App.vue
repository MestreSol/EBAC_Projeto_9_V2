<script setup lang="ts">
import { ref } from 'vue';
import Inputs from './components/Inputs.vue';
import LCD from './components/LCD.vue';

const lcdDisplay = ref('lcd'); // Estado reativo compartilhado
</script>

<template>
  <div class="container">
    <div class="calculator">
      <div class="input-grid">
        <Inputs :lcdDisplay="lcdDisplay"> </Inputs>
      </div>
    </div>
  </div>
</template>

<style scoped>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body{
  font-family: 'Roboto', sans-serif;
  background-color: #f2f2f2;
}

.container{
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.calculator{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: #f2f2f2;
  border: 1px solid #ccc;
  border-radius: 10px;
  width: 50vw;
  height: 75vh;
  margin: 0 auto;
  margin-top: 50px;
}

.tela{
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #f2f2f2;
  border: 1px solid #ccc;
  border-radius: 10px;
  width: 250px;
  height: 100px;
  margin: 0 auto;
  top:0px;
  
}

</style>
