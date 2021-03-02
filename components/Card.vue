<template>
  <div>
    <v-card v-for="(card, index) in cardDatas" max-width="360" :key="index" class="pa-4 pt-2 mb-4">
      <v-row no-gutters class="pa-0 pb-2">
        <v-col
          cols="9"
          class="grabbingArea pa-0"
        /></v-col>
        <v-col cols="3" class="px-0">
          <v-btn small icon class="pa-0">
            <v-icon class="text-right" color="gray400" @click="editCard"> mdi-pencil </v-icon>
          </v-btn>
          <v-btn small icon class="pa-0" @click="deleteCard">
            <v-icon class="text-right" color="gray400"> mdi-close </v-icon>
          </v-btn>
        </v-col>
      </v-row>
      <v-divider class="mb-2" />
      <v-row no-gutters class="ma-0 pa-0">
        <v-col cols="4" align-self="center">
          <p class="date-time warning--text ma-0 font-weight-bold">
            {{ card.due }}
          </p>
        </v-col>
        <v-col cols="7" align-self="center">
          <span class="date-time warning--text font-weight-bold text-h2">{{
            card.time
          }}</span>
        </v-col>
        <v-col cols="1" align-self="center">
          <v-icon
            class="date-time warning--text font-weight-bold text-h3 align-center">
            mdi-alert-rhombus
          </v-icon>
        </v-col>
      </v-row>
      <v-row no-gutters>
        <v-col cols="12">
          <v-chip
            v-for="(chip) in card.chips"
            :key="chip.id"
            class="mr-2 text--text"
            color="gray300"
          >
            {{ chip.title }}
          </v-chip>
        </v-col>
      </v-row>
    </v-card>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from '@nuxtjs/composition-api'

export default defineComponent({
  name: 'Card',
  setup () {
    const date = ref<string>('2021.12.31')
    const time = ref<string>('23:59')

    const cardDatas = [
      {
        id: 1,
        due: '2021.12.31',
        time: '23:59',
        isDead: true,
        createdAt: '',
        updatedAt: '',
        isDone: false,
        chips: [{
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
        }]
      },
      {
        id: 2,
        due: '2021.03.31',
        time: '20:30',
        isDead: false,
        createdAt: '',
        updatedAt: '',
        isDone: false,
        chips: [{
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
        }]
      },
      {
        id: 3,
        due: '2021.04.01',
        time: '23:59',
        isDead: false,
        createdAt: '',
        updatedAt: '',
        isDone: false,
        chips: [{
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
        }]
      },
      {
        id: 4,
        due: '2021.10.11',
        time: '23:59',
        isDead: true,
        createdAt: '',
        updatedAt: '',
        isDone: false,
        chips: [{
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
        }]
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
      editCard,
      deleteCard,
      cardDatas
    }
  }
})
</script>

<style scoped>
.date-time {
  font-family: "Lato", sans-serif;
}
</style>
