<template>
  <v-card class="pa-4" max-width="320">
    <v-row no-gutters class="pb-2">
      <v-spacer />
      <v-btn icon class="pa-0">
        <v-icon class="text-right" color="gray400" @click="editCard"> mdi-pencil </v-icon>
      </v-btn>
      <v-btn icon class="pa-0" @click="deleteCard">
        <v-icon class="text-right" color="gray400"> mdi-close </v-icon>
      </v-btn>
    </v-row>
    <v-divider class="mb-2" />
    <v-row no-gutters>
      <v-col cols="4" align-self="center">
        <p class="date-time warning--text ma-0 font-weight-bold">
          {{ date }}
        </p>
      </v-col>
      <v-col cols="6" align-self="center">
        <span class="date-time warning--text font-weight-bold text-h2">{{
          time
        }}</span>
      </v-col>
      <v-col cols="2" align-self="center">
        <v-icon
          class="date-time warning--text font-weight-bold text-h3 align-center">
          mdi-alert-rhombus
        </v-icon>
      </v-col>
    </v-row>
    <v-row no-gutters>
      <v-col cols="12">
        <v-chip
          v-for="(chip) in demoChips"
          :key="chip.id"
          class="mr-2 text--text"
          color="gray300"
        >
          {{ chip.title }}
        </v-chip>
      </v-col>
    </v-row>
  </v-card>
</template>

<script lang="ts">
import { defineComponent, ref } from '@nuxtjs/composition-api'

export default defineComponent({
  name: 'Card',
  setup () {
    const date = ref<string>('2021.12.31')
    const time = ref<string>('23:59')

    // あとで消す
    const demoChips = [
      {
        id: 1,
        title: '在庫整理'
      },
      {
        id: 2,
        title: '電話'
      },
      {
        id: 3,
        title: '吉田さん'
      }
    ]

    const editCard = () => {
      console.debug('編集処理')
    }
    const deleteCard = () => {
      console.debug('削除処理')
    }

    return {
      date,
      time,
      demoChips,
      editCard,
      deleteCard
    }
  }
})
</script>

<style scoped>
.date-time {
  font-family: "Lato", sans-serif;
}
</style>
