<template>
  <v-container class="pa-0 ma-0" fluid>
    <v-container fluid>
      <Card />
    </v-container>
    <AddCardBtn :open-add-card-dialog="addCard" />
    <CardDialog :is-opened="isOpenAddCardDialog" :cancel-action="() => (isOpenAddCardDialog = false)" />
  </v-container>
</template>

<script lang="ts">
import { defineComponent, ref } from '@nuxtjs/composition-api'

export default defineComponent({
  layout: 'user',
  setup() {
    const isOpenAddCardDialog = ref(false)
    const addCard = () => {
      isOpenAddCardDialog.value = !isOpenAddCardDialog.value
    }

    return {
      addCard,
      isOpenAddCardDialog
    }
  }
})
</script>
