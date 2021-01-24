<template>
  <v-container>
    <v-row no-gutters>
      <v-col cols="12">
        <v-card class="mx-auto pa-6">
          あああ
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { defineComponent } from '@nuxtjs/composition-api'

export default defineComponent({
  setup (_, { root }) {
    const test = 'aaa'

    return {
      test
    }
  }
})
</script>
