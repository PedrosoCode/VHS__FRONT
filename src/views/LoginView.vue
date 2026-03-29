<script setup lang="ts">
import { ref } from 'vue'

const empresas = ref([
  { title: 'suporte', value: 'suporte' },
  { title: 'industria', value: 'industria' },
  { title: 'varejo', value: 'varejo' },
])

const empresa = ref('')
const usuario = ref('')
const senha = ref('')
</script>

<template>
  <v-app>
    <v-main>
      <v-container fluid class="fill-height d-flex align-center justify-center pa-4">
        <v-row class="w-100 justify-center">
          <v-col cols="12" sm="10" md="8" lg="6" xl="4" class="d-flex justify-center">
            <v-card class="w-100 pa-6" style="max-width: 480px;" rounded="xl" elevation="8">
              <v-card-title class="text-h5 font-weight-bold pb-4">
                Login
              </v-card-title>

              <v-card-text class="pt-0">
                <v-form>
                  <v-select
                    label="Empresa"
                    :items="['suporte', 'industria', 'varejo']"
                    class="mb-4"
                    variant="outlined"
                  />

                  <v-text-field
                    label="Usuário"
                    class="mb-4"
                    variant="outlined"
                  />

                  <v-text-field
                    label="Senha"
                    type="password"
                    class="mb-4"
                    variant="outlined"
                  />

                  <v-btn block color="primary" size="large" rounded="lg">
                    Entrar
                  </v-btn>
                </v-form>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>