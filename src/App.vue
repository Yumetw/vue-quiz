<template>
  <GameForm/>
</template>

<script>
import GameForm from "@/components/GameForm";

export default {
  name: 'App',
  components: {
    GameForm,
  },
}
</script>

<style>
body {
  margin: 0;
  background: radial-gradient(40% 50%, #5b85aa, #414770);;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  width: 100vw;
}

#app {
  width: 500px;
  border-radius: 30px;
  padding: 40px;
  background-color: #fff;
  position: relative;
}
</style>
