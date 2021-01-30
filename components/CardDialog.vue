<template>
  <v-row justify="center">
    <v-dialog :value="isOpened" scrollable>
      <v-card class="pa-8">
        <v-row>
          <v-spacer />
          <v-icon class="gray400--text text-right" @click="cancelAction">
            mdi-close-circle-outline
          </v-icon>
        </v-row>
        <v-card-title
          class="pa-0 primary--text font-weight-bold"
        >
          日付
        </v-card-title>
      </v-card>
    </v-dialog>
  </v-row>
</template>

<script lang="ts">
import { defineComponent } from '@nuxtjs/composition-api'

export default defineComponent({
  props: {
    isOpened: {
      type: Boolean,
      default: false
    },
    cancelAction: {
      type: Function,
      default: () => {}
    },
    okAction: {
      type: Function,
      default: () => {}
    }
  }
})
</script>
