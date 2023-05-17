<template>
  <section class="create-player">
    <h3 class="create-player__title">Добавить нового игрока</h3>

    <div class="create-player__form">
      <input
          v-model="playersName"
          class="create-player__input create-player__input_name"
          placeholder="Имя"
      />

      <input
          v-model="playersLife"
          class="create-player__input create-player__input_life"
          placeholder="Жизней"
          type="number"
      />

      <button
          class="create-player__form-btn"
          type="button"
          @click="createPlayer"
      >
        Создать
      </button>
    </div>
  </section>
</template>


<script>
export default {
  name: 'CreatePlayer',
  emit: [
    'playerCreate',
  ],
  data() {
    return {
      players: [],
      playersName: '',
      playersLife: '',
    };
  },
  methods: {
    createPlayer() {

      if(this.playersName === '' || this.playersName === undefined) {
        alert('Укажите имя');
        return;
      }

      if(this.playersLife === '' || this.playersLife === undefined) {
        alert('Укажите количество жизней');
        return;
      }

      if(this.playersLife <= 0) {
        alert('Количество жизней не может быть меньше нуля');
        return;
      }

      this.players.push({
        name: this.playersName,
        life: this.playersLife,
      });

      this.playersName = '';
      this.playersLife = '';

      this.$emit('playerCreate', this.players);
    },
  },
};
</script>

<style lang="scss">
  .create-player {
    &__form {
      display: flex;
      gap: 20px;
      margin: 20px 0;
    }

    &__input {
      width: 100%;
      padding: 10px 15px;
      border: 2px solid orange;
      border-radius: 5px;

      &_life {
        width: 170px;
      }
    }

    &__form-btn {
      padding: 10px 15px;
      background: orange;
      color: white;
      border-color: orange;
      font-weight: bold;
      border-radius: 5px;
    }
  }
</style>
