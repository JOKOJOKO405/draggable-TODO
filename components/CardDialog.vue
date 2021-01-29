<template>
  <v-row justify="center">
    <v-dialog v-model="isOpen" scrollable max-width="300px">
      <v-card>
        <v-card-title>Select Country</v-card-title>
        <v-divider />
        <v-card-text style="height: 300px">
          <v-radio-group column />
        </v-card-text>
        <v-divider />
        <v-card-actions>
          <v-btn color="blue darken-1" text @click="dialog = false">
            Close
          </v-btn>
          <v-btn color="blue darken-1" text @click="dialog = false">
            Save
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>
</template>

<script lang="ts">
import { defineComponent, ref } from '@nuxtjs/composition-api'

export default defineComponent({
  props: {
    isOpen: {
      type: Boolean,
      default: false
    }
  },
  setup (_, { root }) {
    return {
    }
  }
})
</script>
