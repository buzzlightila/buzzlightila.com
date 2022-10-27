<script setup>
import Terminal from '../components/Terminal.vue'
</script>
<template>
  <main>
    <div id="terminals">
    <Terminal command="aboutme" screen_w="400px" screen_h="150px" :command_result="about_me"/>
    <Terminal command="hobbies" screen_w="300px" screen_h="190px" command_result="I love to practice sports like muaythai 🥊, ride bike 🚲 and adventures. Passionate about games like League of legends, fortnite and play xbox games."/>
    <Terminal command="uname -a" screen_w="300px" screen_h="130px" command_result="Atila Rangel Araujo, 08.09.1998"/>
    <Terminal command="contact" screen_w="350px" screen_h="130px" command_result="email: superatilrangel@gmail.com linkedin: linkedin.com/in/buzzlightila/"/>
  </div>
  </main>
</template>
<script>
export default {
  data: () => ({
    about_me: `Hey! I'm adventure and cool software developer with {year_experience} years experience, passionate about Software Development and CyberSecurity.`,
  }),
  created() {
      // about me 
      var year_experience = new Date().getFullYear() -  2016
      this.about_me = this.about_me.replace("{year_experience}", year_experience)
  }
}
</script>

<style>
#terminals{
  position: fixed;
  width: 100%;
  top: 65px;
  left: 0px;
}

@media only screen and (max-width: 600px) {
  #terminals{
    position: absolute;
    width: 100%;
    top: 20px;
    left: 0px;
  }
}
</style>