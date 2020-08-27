<template>
  <div id="app">
    <br />
    <img class="" src="./assets/pngegg.png" width="20%" />
    
    <br />
    <br>
    <h1 class="text-light">Ninja Battle</h1>
    <div>
      <botton />
    </div>
  </div>
</template>
<script>
import botton from "./components/botton.vue";
export default {
  name: "App",
  components: {
    
    botton,
  },
};
</script>

<style>

#app {
  
  height: 100%;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  position: relative;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #e4eaf0;

}

body {
  background-image: url(https://i.pinimg.com/originals/6d/a3/0b/6da30bc0bc0a8f355543ac42bd32372d.png);
  background-attachment: fixed;
  background-repeat: no-repeat;
  background-size: 100% 100%;
  height: 100vh;
}

</style>

