<script lang="ts" setup>
import { shallowRef } from 'vue'

const bMenuAberto = shallowRef(true)
</script>

<template>

<v-app-bar>
  <template v-slot:prepend>
    <v-app-bar-nav-icon @click="bMenuAberto = !bMenuAberto"></v-app-bar-nav-icon>
  </template>

  <v-app-bar-title>Application Bar</v-app-bar-title>
</v-app-bar>

<v-navigation-drawer :width="400" v-model="bMenuAberto">
  <v-list-item title="My Application" subtitle="Vuetify"></v-list-item>
  <v-divider></v-divider>
  <v-list-item link title="List Item 1"></v-list-item>
  <v-list-item link title="List Item 2"></v-list-item>
  <v-list-item link title="List Item 3"></v-list-item>
</v-navigation-drawer>


</template>