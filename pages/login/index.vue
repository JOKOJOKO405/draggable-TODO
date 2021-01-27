<template>
  <v-container>
    <v-row no-gutters align="center">
      <v-col cols="12">
        <v-card class="mx-auto mt-10 px-8 py-10" elevation="4" max-width="480">
          <h1 class="primary--text text-center mb-8">ログイン</h1>
          <v-form ref="form" v-model="valid" lazy-validation @submit.prevent="validateForm">
            <v-text-field
              v-model="name"
              :rules="nameRules"
              label="メールアドレス"
              required
              placeholder="メールアドレス"
            />
            <v-text-field
              v-model="pass"
              :append-icon="showPass ? 'mdi-eye' : 'mdi-eye-off'"
              :rules="passRules"
              :type="showPass ? 'text' : 'password'"
              class="mb-16"
              label="パスワード"
              placeholder="半角英数字12文字以内"
              required
              @click:append="showPass = !showPass"
            />
            <v-col cols="6" class="mx-auto pa-0">
              <v-btn
                color="primary"
                block
                large
                class="font-weight-bold text-h6 pa-4 mb-4"
                elevation="0"
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
import { defineComponent, ref, SetupContext } from '@nuxtjs/composition-api'

export default defineComponent({
  setup (_, { root }) {
    const name = ref<string>('')
    const pass = ref<string | number>('')
    const valid = true
    const showPass = ref(false)
    const form = ref<HTMLFormElement>()

    const nameRules = [
      (v: any) => !!v || '入力必須項目です',
      (v: any) => {
        const regex = /^(([^<>()[\]\\.,;:\s@]+(\.[^<>()[\]\\.,;:\s@]+)*)|(.+))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
        return regex.test(v) || 'メールアドレスが正しくありません'
      }
    ]

    const passRules = [
      (v: any) => !!v || '入力必須項目です',
      (v: any) => /^[\w-]{8,12}$/.test(v) || '8文字以上12文字以内の半角英数字で入力してください',
      (v: any) => {
        const regex = /^[A-Za-z0-9]*$/
        return regex.test(v) || '半角英数字で入力してください'
      }
    ]

    const validateForm = () => {
      const target: any = form.value
      console.debug(target)
      target.validate()
    }

    return {
      showPass,
      valid,
      name,
      pass,
      nameRules,
      passRules,
      form,
      validateForm
    }
  }
})
</script>
