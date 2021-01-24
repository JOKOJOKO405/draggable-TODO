<template>
  <v-container>
    <v-row no-gutters>
      <v-col cols="12">
        <v-card class="mx-auto pa-6">
          <h1 class="text--text text-center mb-8">ログイン</h1>
          <v-form ref="form" v-model="valid" lazy-validation>
            <v-text-field
              v-model="name"
              :rules="nameRules"
              label="ユーザー名"
              required
            />
          </v-form>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { defineComponent } from "@nuxtjs/composition-api";

export default defineComponent({
  setup(_, { root }) {
    const test = "aaa";

    return {
      test,
    };
  },
});
</script>
