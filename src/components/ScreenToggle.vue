<template>
  <div class="screen-toggle">
    <button
      type="button"
      class="screen-toggle__button"
      :class="createButtonExtraClasses"
      @click="$emit('update:modelValue', SCREEN_CREATE)"
    >
      Создание
    </button>
    /
    <button
      type="button"
      class="screen-toggle__button"
      :class="editButtonExtraClasses"
      @click="$emit('update:modelValue', SCREEN_EDIT)"
    >
      Редактирование
    </button>
  </div>
</template>

<script>
import {
  SCREEN_CREATE,
  SCREEN_EDIT,
} from '../App';

export default {
  name: 'ScreenToggler',

  emits: ['update:modelValue'],

  props: {
    modelValue: String,
  },

  data() {
    return {
      SCREEN_CREATE,
      SCREEN_EDIT,
    };
  },

  computed: {
    createButtonExtraClasses() {
      return { 'screen-toggle__button--current': this.modelValue === SCREEN_CREATE };
    },
    editButtonExtraClasses() {
      return { 'screen-toggle__button--current': this.modelValue === SCREEN_EDIT };
    },
  },
};
</script>

<style lang="scss">
  .screen-toggle {
    margin-bottom: 100px;

    &__button {
      padding: 10px 15px;
      border: 1px orange solid;
      font-weight: bold;
      background-color: white;
      border-radius: 20px;

      &--current {
        background: orange;
        color: white;
      }
    }
  }
</style>
