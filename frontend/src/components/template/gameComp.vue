<template>
  <div v-if="clip.length" class="game">
    <audio src=""></audio>
    <div class="player">
      <video :src="clip[0].url" autoplay muted loop></video>
    </div>
    <div class="btn-group">
      <buttonComp label="Dica" hit />
      <buttonComp label="Confirmar" confirm />
      <buttonComp label="Próximo" next />
    </div>
    <div class="input">
      <input type="search" name="" id="" v-model="text" @keydown="show = true"/>
      <ul v-show="show">
        <li
          v-for="(lister, index) in list"
          :key="index"
          v-show="lister.music_name.includes(text)"
        >
          <a @click="updateTextAndShowOff(lister.music_name)">{{ lister.music_name }}</a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import api from "@/services/api.js";
import buttonComp from "../buttonComp.vue";
export default {
  name: "gameComp",
  components: {
    buttonComp,
  },
  data() {
    return {
      clip: [],
      list: [],
      text: "",
      show: false,
      readyData: false,
      currentIndex: 0
    };
  },
  async mounted() {
    this.loadList();
    this.loadClip();
    // this.readyData = true
  },
  methods: {
    async loadList() {
      const url = "/musics";
      const response = await api.get(url);
      this.list = response.data;
    },
    async loadClip() {
      const url = "/clips";
      const response = await api.get(url);
      this.clip = response.data;
    },
    // loadList() {
    //   const url = "/musics";
    //   api
    //     .get(url)
    //     .then((response) => {
    //       this.list = response.data;
    //     })
    // },
    // loadClip() {
    //   const url = "/clips";
    //   api
    //     .get(url)
    //     .then((response) => {
    //       this.clip = response.data;
    //     })
    // },
    updateTextAndShowOff(newText) {
        this.text = newText
        this.show = false
    },
  },
};
</script>

<style>
* {
  margin: 0px;
  box-sizing: border-box;
  padding: 0;
  outline: 0;
}

.game {
  display: flex;
  flex-direction: column;
  width: 600px;
  height: 450px;
  border: 2px solid black;
  justify-content: center;
  align-items: center;
}

.player {
  width: 500px;
  height: 200px;
}

.player video {
  width: 100%;
  height: 100%;
}

.input {
  overflow: auto;
  max-height: 150px;
  width: 250px;
}

.input input {
    width: 100%;
    border: 3px solid black;
    border-radius: 9px;
}

.input li {
    list-style: none;
    width: 100%;
    margin-top: 3px;
}

.input a {
    width: 100%;
    display: flex;
    flex-direction: column;
}

::-webkit-scrollbar {
    width: 5px;
    background-color: #cdc6ac; 
}

::-webkit-scrollbar-thumb{
    background-color: #816477; 
    border-radius: 10px;
}

.input a:hover {
    background-color: #b0a19d;
}
</style>