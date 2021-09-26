<template>
<div class = "container">
  <div class = "page">
    <div class = "star-page"/>
    <div class = "star-port"/>
    <div class="music-player">
    <button class = "music" @click="playSound(require('./assets/space.mp3'))">Launch Mission</button>
    <div @click="toggleSound()" class="toggle-sound"></div>
  </div>

    <div id = app>
      <Header 
                @toggle-add-task="toggleAddTask" 
                :showAddTask = "showAddTask"
              />
        <router-view :showAddTask="showAddTask"></router-view>
      <Footer/>
    </div>
    <a href = "https://andrewsandell.com" class = "button">Return to AndrewSandell.com</a>
  </div>
</div>

</template>

<script>
import Header from './components/Header'
import Footer from './components/Footer'

export default {
  name: 'App',
  components: {
    Header,
    Footer,
  },
  data() {
    return {
      showAddTask: false,
    }
  },
  methods:{
    toggleAddTask(){
      var openAudio = new Audio(require('./assets/bleep.wav'))
      openAudio.play()
      this.showAddTask = !this.showAddTask
    },
    playSound(sound){
      if(sound){
        var audio = new Audio(sound);
        audio.play();
      }
    }
  },
  mounted: function(){
    var audio = new Audio('./assets/space.mp3');
    audio.play();
  }
}
</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
  
}
.page {
  height: 100%;
  width: auto;
  font-family: 'Poppins', sans-serif;
  overflow-y: hidden;
}

.container{
  overflow-y: hidden;
}
.star-page {
  left: 0px;
  top: 0px;
  z-index: -1;
  height: 1080px;
  width: 1920px;
  background-image: url("./assets/stars-space.gif");
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  position: absolute;
}
.star-port{
  z-index: 1;
  height: 1080px;
  width: 1920px;
  background-image:url('./assets/Transparent Viewport.png');
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  position: absolute;
  
}
.music{
  height: 200px;
  width:  200px;
  position: absolute;
  z-index: 80;
  background-color: green;
  border-radius: 50%;
  top: 360px;
  left: 30px;
  font-size: 30px;
  font-weight: 800;
}
#app{
  z-index: 5;
  position: absolute;
  max-height: 1080px;
  
}

.taskbar {
  position: relative;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
a.button{
  position: absolute;
  z-index: 5;
  text-align: center;
  background-color: black;
  padding: 10px;
  border-radius: 25%;
  left: 46px;
  top: 68px;

  -webkit-appearance: button;
  -moz-appearance: button;
  appearance: button;
  text-decoration: none;
  color: rgb(0,162,232);
}
</style>
