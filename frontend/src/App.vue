<template>
  <router-view />
</template>

<script>

export default {
  name: "App",
  components: {},
};
</script>

<style>
body {
  margin: 0;
  background: linear-gradient(to right, #e0e1d8, #cdc6ac, #b0a19d, #816477);
}
#app {
  display: flex;
  flex-direction: column;
  height: 100vh;
  justify-content: center;
  align-items: center;
}
</style>
