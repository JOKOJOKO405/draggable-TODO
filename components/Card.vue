<template>
  <v-card class="pa-4" max-width="320">
    <v-row no-gutters class="pb-2">
      <v-col align-self="center">
        <v-rating
          length="5"
          readonly
          background-color="accent"
          color="accent"
          size="20"
          value="3"
          dense
        />
      </v-col>
      <v-spacer />
      <v-btn icon class="pa-0">
        <v-icon class="text-right" color="gray400">
          mdi-bell-outline
        </v-icon>
      </v-btn>
      <v-btn icon class="pa-0">
        <v-icon class="text-right" color="gray400">
          mdi-pencil
        </v-icon>
      </v-btn>
      <v-btn icon class="pa-0">
        <v-icon class="text-right" color="gray400">
          mdi-close
        </v-icon>
      </v-btn>
    </v-row>
    <v-divider class="mb-2" />
    <v-row no-gutters align="center">
      <v-col cols="12" class="d-flex">
        <span class="date-time warning--text font-weight-bold align-center">{{ date }}</span>
        <span class="date-time warning--text font-weight-bold text-h2">{{ time }}</span>
        <v-icon class="date-time warning--text font-weight-bold text-h3 align-center">mdi-alert-rhombus</v-icon>
      </v-col>
    </v-row>
  </v-card>
</template>

<script lang="ts">
import { defineComponent, ref } from '@nuxtjs/composition-api'

export default defineComponent({
  name: 'Card',
  setup(_, { root }) {
    const date = ref<string>('2021.01.31')
    const time = ref<string>('23:59')

    return {
      date,
      time
    }
  }
})
</script>

<style scoped>
.date-time{
  font-family: 'Lato', sans-serif;
}
</style>
