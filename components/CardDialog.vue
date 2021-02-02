<template>
  <v-dialog :value="isOpened" scrollable max-width="600">
    <v-card class="pa-8">
      <v-row>
        <v-spacer />
        <v-icon large class="gray400--text text-right" @click="cancelAction">
          mdi-close-circle-outline
        </v-icon>
      </v-row>
      <v-form>
        <v-card-title class="pa-0 primary--text font-weight-bold">
          日時
        </v-card-title>
        <v-row no-gutters class="mb-8">
          <v-col cols="6">
            <v-text-field
              type="date"
              class="pr-4 ma-0"
            />
          </v-col>
          <v-col cols="6">
            <v-text-field
              type="time"
              class="pl-4 ma-0"
            />
          </v-col>
        </v-row>
        <v-card-title class="pa-0 primary--text font-weight-bold">
          内容
        </v-card-title>
        <v-row no-gutters class="mb-8">
          <v-col cols="12">
            <v-text-field
              type="text"
              class="pa-0"
            />
            <v-chip
              v-for="(chip) in demoChips"
              :key="chip.id"
              class="mr-4 primary--text"
              color="#DAF9F1"
            >
              {{ chip.title }}
            </v-chip>
          </v-col>
        </v-row>
        <v-card-title class="pa-0 primary--text font-weight-bold mb-4">
          カードの色
        </v-card-title>
        <v-row no-gutters class="mb-8">
          <v-col cols="12">
            <v-btn
              v-for="(color, index) in cardColors"
              :key="index"
              class="mr-4"
              fab
              x-small
              depressed
              :style="color.style"
              :color="color.name"
            />
          </v-col>
        </v-row>
        <v-card-title class="pa-0 primary--text font-weight-bold">
          通知
        </v-card-title>
        <v-row no-gutters class="mb-8" align="center">
          <v-col cols="2">
            <v-text-field
              type="number"
              class="mr-4"
            />
          </v-col>
          <v-col cols="2">
            <v-select
              :items="dates"
              class="mr-4"
            />
          </v-col>
          <v-col cols="2">前から</v-col>
        </v-row>
      </v-form>
    </v-card>
  </v-dialog>
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
  },
  setup (_, { root }) {
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
    const cardColors = [
      {name: 'white', style: 'border: 1px solid #BDBDBD !important;'},
      {name: '#FFF9E4'},
      {name: '#F4FFEC'},
      {name: '#E9FFFA'},
      {name: '#FFE9EE'},
      {name: '#FFF3E9'},
      {name: '#F7E9FF'}
    ]

    const dates = [
      '日',
      '時間'
    ]

    return {
      demoChips,
      cardColors,
      dates
    }
  }
})
</script>
