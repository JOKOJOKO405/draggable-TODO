<template>
  <v-card id="card" class="pa-4 pt-2" :style="cardPosition">
    <v-row no-gutters class="pa-0 pb-2">
      <v-col
        cols="9"
        class="grabbingArea pa-0"
        @mousedown="onMouseDown"
        @mouseup="onMouseUp"
        @dragstart="onDragStart"
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
          {{ date }}
        </p>
      </v-col>
      <v-col cols="7" align-self="center">
        <span class="date-time warning--text font-weight-bold text-h2">{{
          time
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
import { defineComponent, ref, computed } from '@nuxtjs/composition-api'

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

    // カーソル表示
    const isGrabbing = ref(false)
    const top = ref('50%')
    const left = ref('50%')
    const shiftX = ref(0)
    const shiftY = ref(0)
    // カードのポジション
    const cardPosition = computed(() => {
      return `position:absolute; left:${left.value}; top:${top.value}; cursor: ${isGrabbing.value ? 'grabbing' : 'grab'}`
    })

    const editCard = () => {
      console.debug('編集処理')
    }
    const deleteCard = () => {
      console.debug('削除処理')
    }

    const onMouseDown = (event: any) => {
      isGrabbing.value = true
      console.debug('run')
      shiftX.value = event.clientX - event.target.closest('#card').getBoundingClientRect().left
      shiftY.value = event.clientY - event.target.closest('#card').getBoundingClientRect().top
      moveCard(event.clientX, event.clientY)
      document.addEventListener('onmousedown', onMouseDown)
    }

    const onMouseUp = () => {
      isGrabbing.value = false
      document.removeEventListener('onmouseup', onMouseUp)
    }

    const moveCard = (leftP: number, topP: number) => {
      left.value = leftP - shiftX.value + 'px'
      top.value = topP - shiftY.value + 'px'
    }

    const onDragStart = () => false

    return {
      date,
      time,
      demoChips,
      editCard,
      deleteCard,
      onMouseDown,
      onMouseUp,
      cardPosition,
      onDragStart
    }
  }
})
</script>

<style scoped>
.date-time {
  font-family: "Lato", sans-serif;
}
</style>
