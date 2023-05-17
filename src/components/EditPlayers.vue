<template>
  <section class="edit-players">
    <h3 class="edit-players__title">Редактирование игроков</h3>

    <div class="edit-players__players-list">
      <div
          v-for="player in players"
          :key="player.name"
          class="edit-players__player-form"
      >
        <input class="edit-players__player-form-input" v-model="player.name">
        <div class="edit-players__player-life-counter">
          <button class="edit-players__player-life-counter-btn" @click="minusLife(player)">-</button>
          <span class="edit-players__player-life-counter-value">{{player.life}}</span>
          <button class="edit-players__player-life-counter-btn" @click="plusLife(player)">+</button>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'EditPlayers',
  props: {
    modelValue: Array,
  },
  data() {
    return {
      players: this.modelValue,
    };
  },
  methods: {
    plusLife (item) {
      item.life++;
      this.$emit('update:modelValue', this.players);
    },
    minusLife (item) {
      item.life--;
      this.$emit('update:modelValue', this.players);
    },
  },
};
</script>

<style lang="scss">
  .edit-players {
    &__player-form {
      display: flex;
      align-items: center;
      margin-top: 20px;

      &-input {
        width: 100%;
        padding: 10px 15px;
        border: 2px solid orange;
        border-radius: 5px;
        margin-right: 25px;
      }
    }
    &__player-life-counter {
      display: flex;
      align-items: center;

      &-value {
        margin: 0 12px;
      }

      &-btn {
        width: 25px;
        background: orange;
        color: white;
        border-color: orange;
        font-weight: bold;
        border-radius: 5px;
        padding: 5px;
      }
    }
  }
</style>
