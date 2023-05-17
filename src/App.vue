<template>
  <ScreenToggle v-model="currentScreen" />
  <CreatePlayer
    v-if="isScreenCreate"
    @playerCreate="handlePlayerCreate" />
  <EditPlayers
    v-if="isScreenEdit"
    v-model="playersList"
    @playersUpdate="handlePlayersUpdate" />
  <RatingOfPlayers :playersList="playersList" />
</template>

<script>
import ScreenToggle from "./components/ScreenToggle";
import CreatePlayer from './components/CreatePlayer.vue';
import EditPlayers from './components/EditPlayers.vue';
import RatingOfPlayers from "./components/RatingOfPlayers";

export const SCREEN_CREATE = 'SCREEN_CREATE';
export const SCREEN_EDIT = 'SCREEN_EDIT';

export default {
  name: 'App',
  components: {
    ScreenToggle,
    CreatePlayer,
    EditPlayers,
    RatingOfPlayers,
  },
  data() {
    return {
      currentScreen: SCREEN_CREATE,
      playersList: [],
    };
  },
  computed: {
    isScreenCreate() {
      return this.currentScreen === SCREEN_CREATE;
    },
    isScreenEdit() {
      return this.currentScreen === SCREEN_EDIT;
    },
  },
  methods: {
    handlePlayerCreate(newPlayers) {
      this.playersList = newPlayers;
    },
    handlePlayersUpdate(newPlayers) {
      this.playersList = newPlayers;
    },
  },
};
</script>

<style lang="scss">
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin: 60px auto;
    width: 800px;
  }
</style>
