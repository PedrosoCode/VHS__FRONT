<template>
  <v-container class="fill-height">
    <v-row align="center" justify="center">
      
      <!-- Lado esquerdo -->
      <v-col cols="12" md="6">
        <div class="text-left">
          <h1 class="text-h3 font-weight-bold mb-4">
            Chat de suporte de chamados
          </h1>

          <p class="text-subtitle-1 text-medium-emphasis">
            Gerencie atendimentos, organize conversas e acompanhe seus chamados
            em tempo real de forma simples e eficiente.
          </p>
        </div>
      </v-col>

      <!-- Lado direito -->
      <v-col cols="12" md="6" class="text-center">
        <v-btn
          color="primary"
          size="x-large"
          rounded="xl"
          elevation="4"
          @click="$router.push('/login')"
        >
          Iniciar atendimento
        </v-btn>
      </v-col>

    </v-row>
  </v-container>
</template>

<script setup lang="ts">
</script>

<style scoped>
.fill-height {
  min-height: 100vh;
}
</style>