<template>
  <section class="rating">
    <h3 class="rating__title">Рейтинг</h3>

    <table class="rating__table">
      <tr
          v-for="(item, index) in rating"
          :key="index"
      >
        <td v-text="`${index + 1}`"></td>
        <td v-html="getItem(item.name, item.life)"></td>
      </tr>
    </table>
  </section>
</template>

<script>
export default {
  name: 'RatingOfPlayers',
  props: {
    playersList: {
      type: Array,
      required: true
    },
  },
  computed: {
    rating() {
      return [...this.playersList].sort((a, b) => b.life - a.life);
    },
  },
  methods: {
    getItem(name,life) {
      return `У игрока <b>${name}</b> ${life} жизней`;
    },
  },
};
</script>

<style lang="scss">
  .rating__table {
    width: 100%;

    td {
      border: 1px solid #ddd;
      padding: 15px;
      text-align: left;

      &:first-child {
        text-align: center;
        width: 20px;
      }
    }
  }
</style>
