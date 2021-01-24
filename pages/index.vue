<template>
  <v-row no-gutters>
    test
  </v-row>
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
