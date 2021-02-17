<template>
  <v-btn fab color="primary" elevation="0" class="add-btn" @click="openAddCardDialog">
    <v-icon large>mdi-plus-thick</v-icon>
  </v-btn>
</template>

<script lang="ts">
import { defineComponent } from '@nuxtjs/composition-api'

export default defineComponent({
  props: {
    openAddCardDialog: {
      type: Function,
      default: () => {}
    }
  },
  setup(_, { root }) {

  }
})
</script>

<style scoped>
  .add-btn {
    position: fixed;
    bottom: 24px;
    right: 24px;
  }
</style>