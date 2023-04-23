<script setup>
import Terminal from '../components/Terminal.vue'
</script>
<template>
  <main>
    <div id="terminals">
    <Terminal command="uname --help" screen_w="400px" screen_h="90%" :command_result="about_me"/>
  </div>
  </main>
</template>
<script>
export default {
  data: () => ({
    about_me: [
      {
        title: `aboutme`,
        description: `Experienced cybersecurity engineer and developer with a focus on cryptography with {year_experience} years experience`
      },
      {
        title: `hobbies`,
        description: `I love to practice sports like muaythai 🥊, ride bike 🚲 and adventures. Passionate about games like League of legends, fortnite and play xbox games.`
      },
      {
        title: `contact`,
        description: `linkedin.com/in/buzzlightila`
      },
    
    ]
  }),
  created() {
      // about me 
      var year_experience = new Date().getFullYear() -  2017
      this.about_me[0].description = this.about_me[0].description.replace("{year_experience}", year_experience)
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
</style>