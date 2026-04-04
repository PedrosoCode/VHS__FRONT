<script setup lang="ts">
import { onMounted, onBeforeUnmount } from "vue";

let ws: WebSocket | null = null;

onMounted(() => {
  ws = new WebSocket("ws://localhost:3000/ws");

  ws.onopen = () => {
    console.log("Conectado ao servidor");
    ws?.send("Olá do Vue 🚀");
  };

  ws.onmessage = (event) => {
    console.log("Mensagem recebida:", event.data);
  };

  ws.onclose = () => {
    console.log("Desconectado");
  };
});

onBeforeUnmount(() => {
  ws?.close();
});
</script>

<template>
  <div class="bg-sky-200 p-4">
    <h1>This is an about page</h1>
  </div>
</template>