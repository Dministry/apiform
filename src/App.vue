<template>
  <div id="app">
    <Profile  class="element"/>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import Profile from './components/Profile'

export default {
  name: "Home",
  components: {
    Profile
  }
}
</script>

<style>
html {
  font-family: 'Roboto', sans-serif;
  background-blend-mode:multiply;
  background-repeat: no-repeat;
  margin: 0;
  padding: 0; }
  .element {
  animation: pulse 5s infinite;
}

@keyframes pulse {
  0% {
    background-color: linear-gradient(to right, #428bca, rgb(211, 58, 211));
    height: 100%;
  }
  100% {
    background-color:  rgb(7, 77, 87);
    height: 100%;
  }
}

</style>
