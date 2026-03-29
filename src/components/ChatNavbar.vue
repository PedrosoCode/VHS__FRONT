<script lang="ts" setup>
import { shallowRef } from 'vue'

const bMenuAberto = shallowRef(true)
</script>

<template>

<v-app-bar>
  <template v-slot:prepend>
    <v-app-bar-nav-icon @click="bMenuAberto = !bMenuAberto" >
      
    </v-app-bar-nav-icon>
  </template>

  <v-app-bar-title>Chamado 123 - Suporte Faturamento </v-app-bar-title>

  <template v-slot:append>
    <v-btn icon="mdi-logout"></v-btn>
  </template>

</v-app-bar>

<v-navigation-drawer :width="400" v-model="bMenuAberto">
  <v-list-item title="Anexos" subtitle="arquivos do chamado"></v-list-item>
  <v-divider></v-divider>
  <v-list-item link title="Print erro"></v-list-item>
  <v-list-item link title="Print Tela"></v-list-item>
  <v-list-item link title="XML NFE 836473"></v-list-item>
</v-navigation-drawer>


</template>