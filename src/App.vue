<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HomeView from './views/HomeView.vue';
import TerminalAboutMe from './views/HomeView.vue';

</script>

<template>
  <header>
    <img alt="Buzzlightila logo" class="logo" src="@/assets/logo.png"/>
  </header>
  <HomeView/>
</template>

<style scoped>
header {
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center; 
  overflow: hidden;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
}

.logo {
  margin-top: 20px;
  width: 15%;
  height: auto;
}
</style>
