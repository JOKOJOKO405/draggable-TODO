<template>
  <v-container>
    <v-row no-gutters>
      <v-col cols="12">
        <v-card class="mx-auto pa-6" max-width="480">
          <h1 class="text--text text-center mb-8">ログイン</h1>
          <v-form ref="form" v-model="valid" lazy-validation>
            <v-text-field
              v-model="name"
              :rules="nameRules"
              label="ユーザー名"
              required
            />
            <v-text-field
              v-model="pass"
              class="mb-16"
              :rules="nameRules"
              label="パスワード"
              required
            />
            <v-col cols="6" class="mx-auto pa-0">
              <v-btn
                color="primary"
                block
                large
                class="font-weight-bold text-h6 pa-4 mb-4"
                elevation="0"
                @click="validate"
              >
                ログイン
              </v-btn>
            </v-col>
            <v-col cols="6" class="mx-auto pa-0">
              <v-btn
                color="white"
                outlined
                block
                large
                class="font-weight-bold text-h6 pa-4 primary--text"
                elevation="0"
                @click="validate"
              >
                新規登録
              </v-btn>
            </v-col>
          </v-form>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import { defineComponent, ref } from '@nuxtjs/composition-api'

export default defineComponent({
  setup (_, { root }) {
    const name = ref<string>('ユーザー名')
    const pass = ref<string | number>('')

    return {
      name,
      pass
    }
  }
})
</script>
