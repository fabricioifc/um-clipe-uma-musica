<template>
  <div class="main">
    <h2>Um clipe uma música</h2>
    <router-link to="/game">
        <buttonComp label="Jogar" normal/>
    </router-link>
    <router-link to="/tutorial">
        <buttonComp label="Tutorial" normal/>
    </router-link>
  </div>
</template>

<script>
import buttonComp from '../buttonComp.vue'
export default {
    name: 'mainMenu',
    components: {
        buttonComp
    }
}
</script>

<style>

  @import url('https://fonts.googleapis.com/css2?family=Croissant+One&display=swap');

    .main {
        background-color: rgba(127, 127, 127, 0.4);
        height: 250px;
        width: 300px;
        border: 2px solid black;
        border-radius: 15px;
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .main h2 {
        font-family: 'Croissant One', cursive;
        font-size: 1.5rem;
    }
</style>