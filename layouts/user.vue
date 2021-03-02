<template>
  <v-app>
    <v-main class="pa-0 ma-0">
      <v-app-bar color="white" elevation="1">
        <v-avatar color="accent" size="32">
          <v-icon dark> mdi-account-circle </v-icon>
        </v-avatar>
        <v-toolbar-title class="ml-2">{{ userName }}</v-toolbar-title>
        <v-spacer />
        <v-btn icon color="warning">
          <v-icon>mdi-clock-alert</v-icon>
        </v-btn>
        <v-btn icon>
          <v-icon>mdi-cog</v-icon>
        </v-btn>
        <v-btn icon class="ml-4">
          <v-icon>mdi-logout</v-icon>
        </v-btn>
      </v-app-bar>
      <nuxt />
    </v-main>
  </v-app>
</template>

<script lang="ts">
import { defineComponent, ref } from '@nuxtjs/composition-api'

export default defineComponent({
  setup() {
    const userName = ref<string>('えいじ')

    return {
      userName
    }
  }
})
</script>
