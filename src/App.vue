<template>
  <div class = "page">
    <div class = "star-page"/>
    <div class = "star-port"/>
    <div id = app>
      <Header 
                @toggle-add-task="toggleAddTask" 
                :showAddTask = "showAddTask"
              />
        <router-view :showAddTask="showAddTask"></router-view>

    </div>
  </div>

</template>

<script>
import Header from './components/Header'

export default {
  name: 'App',
  components: {
    Header,
  },
  mounted(){
    this.showPopUp = false
  },
  data() {
    return {
      showAddTask: false,
    }
  },
  methods:{
    toggleAddTask(){
      this.showAddTask = !this.showAddTask
    },
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
body {
  height:1080px;
  width:1920px;
  font-family: 'Poppins', sans-serif;
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
#app{
  z-index: 5;
  position: absolute;
}

.Youtube{
  position:absolute;
  z-index: 99;
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
</style>
