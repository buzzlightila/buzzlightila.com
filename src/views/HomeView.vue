<script setup>
import Terminal from '../components/Terminal.vue'
</script>
<template>
  <main>
    <Terminal command="aboutme" screen_w="400px" screen_h="160px" :command_result="about_me"/>
  </main>
</template>
<script>
export default {
  data: () => ({
    about_me: `Hey! I'm adventure and cool software developer with {year_experience} years experience, passionate about Software Development and CyberSecurity.`,
  }),
  created() {
      // about me 
      var year_experience = new Date().getFullYear() -  2017 
      this.about_me = this.about_me.replace("{year_experience}", year_experience)
  }
}
</script>