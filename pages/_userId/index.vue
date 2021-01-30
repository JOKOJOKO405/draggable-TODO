<template>
  <v-container class="pa-0" fluid>
    <v-app-bar color="white" elevation="1">
      <v-avatar color="accent" size="32">
        <v-icon dark>
          mdi-account-circle
        </v-icon>
      </v-avatar>
      <v-toolbar-title class="ml-2">{{ userName }}</v-toolbar-title>
      <v-spacer></v-spacer>
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
    <v-container>
      <Card />
    </v-container>
    <AddCardBtn :on-click="addCard" />
    <CardDialog
      :is-opened="isOpenAddCardDialog"
    />
  </v-container>
</template>

<script lang="ts">
import { defineComponent, ref } from '@nuxtjs/composition-api'

export default defineComponent({
  setup (_, { root }) {
    const name = ref<string>('ユーザー名')
    const pass = ref<string | number>('')

    const userName = ref<string>('えいじ')

    const isOpenAddCardDialog = ref(false)
    const addCard = () => {
      isOpenAddCardDialog.value = true
    }

    return {
      name,
      pass,
      userName,
      addCard,
      isOpenAddCardDialog
    }
  }
})
</script>
