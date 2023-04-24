<template>
    <div id="screen">
        <div id="bar">
            <div id="icons">
                <div id="red"></div>
                <div id="yellow"></div>
                <div id="green"></div>
            </div>
        </div>
        <p class="font-dir">> root@{{ip}}:~$ <span class="command">{{command}}</span></p>
        <div style="visibility: hidden;" ref="describer"></div>
    </div>
</template>
<script>
import { ref } from 'vue'
export default {
  props: {
    command: String,
    command_result: String,
    screen_w: String,
    screen_h: String
  },
  data: () => ({
    ip: "10.0.0.1",
  }),
  created() {
    fetch("https://api.ipify.org?format=json")
    .then(response => response.json())
    .then(data => (this.ip = data.ip))
    
  },
  mounted() {
    this.command_result.forEach(elm => {
        var p = document.createElement('p')
        p.className = "font-command_result"
        p.innerText = `--${elm.title}\n ${elm.description}`
        this.$refs.describer.append(p)
    })

    // typeAnimation
    const cmd = document.querySelector('.command');
    const cmdChars = [...cmd.textContent.trim()];

    cmd.innerHTML = '';
    let i = 0;
    const timer = setInterval(() => {
    cmd.append(cmdChars[i]);
    if (++i === cmdChars.length) {
        clearInterval(timer);
        setTimeout(() => {
        this.$refs.describer.style.visibility = '';
        }, 400);
    }
    }, 150);


    },
}
</script>
<style>

/* .typingEffect > div {
  padding: 10px;
}

.typingEffect code {
  padding: 0;
  background-color: inherit;
}

.typingEffect code {
  width: fit-content;
  height: fit-content;
  border-right: 2px solid transparent;
}

.typingEffect__line1 {
  animation: blink 1s 2;
} */

#head {
    font-family: monospace;
    margin: auto;
    padding: 35px;
    font-size: 40px;
    text-align: center;
}
#bar {
    text-align: center;
    width: 100%;
    height: 25px;
    background-color: #3B3D3E;
    font-family: monospace;
    border-top-left-radius: 5px;
    border-top-right-radius: 5px;
}
#icons {
    display: flex;
    padding-left: 10px;
    padding-top: 8px;
}
#red {
    background-color: #FF5F57;
    border-radius: 100%;
    width: 10px;
    height: 10px;
    margin-right: 5px;
}
#yellow {
    background-color: #F2AE2E;
    border-radius: 100%;
    width: 10px;
    height: 10px;
    margin-right: 5px;
}
#green {
    background-color: #26BF30;
    border-radius: 100%;
    width: 10px;
    height: 10px;
}
#screen {
    background-color: #000000;
    width: 50%;
    height: auto;
    border-radius: 5px;
    margin: 30px auto;
    box-shadow: 0px 0px 20px rgb(0, 0, 0);
    border: .1px solid rgb(168, 168, 168);
}

.font-dir {
    color: #5EF2F2;
    font-family: monospace;
    font-size: 14px;
    text-align: left;
    position: static;
    padding: 10px 10px 0px 10px;
}
.font-command_result {
    color: #C7C8C8;
    font-family: monospace;
    font-size: 14px;
    text-align: left;
    position: static;
    padding: 0px 10px 10px 10px;
}
.command {
    color: #e6d09e;
}
</style>