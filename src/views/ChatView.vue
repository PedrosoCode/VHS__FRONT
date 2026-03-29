<template>
    <ChatNavbar />

    <v-main>
        <v-container class="fill-height d-flex flex-column pa-4" fluid>

            <!-- CHAT -->
            <v-card class="flex-grow-1 d-flex flex-column" rounded="xl">

                <v-divider />

                <!-- MENSAGENS -->
                <v-card-text class="flex-grow-1 overflow-y-auto">

                    <v-row v-for="msg in messages" :key="msg.id" class="mb-2" :justify="msg.mine ? 'end' : 'start'">
                        <v-col cols="auto" style="max-width: 75%;">
                            <v-sheet :color="msg.mine ? 'primary' : 'grey-lighten-3'"
                                :class="msg.mine ? 'text-white' : ''" rounded="xl" class="pa-3" elevation="2">
                                <div class="text-caption mb-1">
                                    {{ msg.author }} • {{ msg.time }}
                                </div>

                                <div>{{ msg.text }}</div>

                                <div v-if="msg.file" class="text-caption mt-2">
                                    📎 {{ msg.file }}
                                </div>
                            </v-sheet>
                        </v-col>
                    </v-row>

                </v-card-text>

                <v-divider />

                <!-- INPUT -->
                <v-card-actions>
                    <v-row class="w-100" dense>
                        <v-col cols="12">
                            <v-textarea v-model="draftMessage" label="Digite uma mensagem" rows="2" auto-grow
                                variant="outlined" hide-details />
                        </v-col>

                        <v-col cols="4" md="4">
                            <v-file-input v-model="selectedFile" label="Anexar arquivo" prepend-icon="mdi-paperclip"
                                variant="outlined" hide-details />
                        </v-col>

                        <v-col cols="12" md="8">
                            <v-btn block color="primary" size="large" @click="sendMessage">
                                Enviar
                            </v-btn>
                        </v-col>
                    </v-row>
                </v-card-actions>

            </v-card>

        </v-container>
    </v-main>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import ChatNavbar from '@/components/ChatNavbar.vue'

interface ChatMessage {
    id: number
    author: string
    time: string
    text: string
    mine: boolean
    file?: string
}

const messages = ref<ChatMessage[]>([
    {
        id: 1,
        author: 'Pedro',
        time: '09:12',
        text: 'Bom dia! Preciso de ajuda.',
        mine: false,
    },
    {
        id: 2,
        author: 'Você',
        time: '09:13',
        text: 'Claro! Me diga o problema.',
        mine: true,
    },
])

const draftMessage = ref('')
const selectedFile = ref<File[] | File | null>(null)

function sendMessage() {
    if (!draftMessage.value && !selectedFile.value) return

    const now = new Date()
    const time = now.toLocaleTimeString('pt-BR', {
        hour: '2-digit',
        minute: '2-digit',
    })

    const fileName = Array.isArray(selectedFile.value)
        ? selectedFile.value[0]?.name
        : selectedFile.value?.name

    messages.value.push({
        id: Date.now(),
        author: 'Você',
        time,
        text: draftMessage.value || 'Arquivo enviado',
        mine: true,
        file: fileName,
    })

    draftMessage.value = ''
    selectedFile.value = null
}
</script>