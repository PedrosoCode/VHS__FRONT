<script setup lang="ts">
import MainNavbar from '@/components/MainNavbar.vue'

interface intListaChamado {
    Titulo: string,
    UsuarioAbertura: string,
    Empresa: string,
    TipoChamado: string,
    Prioridade: string,
    Status: number,
    Codigo: number,
    CodigoEmpresaChamado: number
}

const objListaChamados: intListaChamado[] = [
    {
        Titulo: 'Erro em importacao de pedido',
        UsuarioAbertura: 'Gerente PDV',
        Empresa: 'Industry',
        TipoChamado: 'Suporte',
        Prioridade: 'Alta',
        Status: 2,
        Codigo: 1,
        CodigoEmpresaChamado: 0
    },
    {
        Titulo: 'Faturamento NF Rejeitada',
        UsuarioAbertura: 'Faturista',
        Empresa: 'Varejo',
        TipoChamado: 'Suporte',
        Prioridade: 'Alta',
        Status: 2,
        Codigo: 2,
        CodigoEmpresaChamado: 0
    },
    {
        Titulo: 'Gráfico de produtividade',
        UsuarioAbertura: 'Owner',
        Empresa: 'Varejo',
        TipoChamado: 'Desenvolvimento',
        Prioridade: 'baixa',
        Status: 3,
        Codigo: 3,
        CodigoEmpresaChamado: 0
    }
]

function BackgroundTable(status: number) {
    switch (status) {
        case 2:
            return 'status-azul'
        case 3:
            return 'status-vermelho'
        default:
            return ''
    }
}

</script>

<template>
    <MainNavbar />

    <v-main>
        <!-- Grupo de inputs -->
        <v-container fluid class="py-8 px-8">
            <v-card class="mx-auto pa-6">
                <v-card-title>Filtros</v-card-title>

                <v-form>
                    <v-row dense>
                        <v-col cols="12" md="4">
                            <v-text-field label="Título" variant="outlined" density="comfortable" />
                        </v-col>

                        <v-col cols="12" md="4">
                            <v-text-field label="Usuário" variant="outlined" density="comfortable" />
                        </v-col>

                        <v-col cols="12" md="4">
                            <v-select label="Empresa" multiple variant="outlined" density="comfortable"
                                :items="['Varejo', 'Industry']" />
                        </v-col>

                        <v-col cols="12" md="4">
                            <v-select label="Tipo" multiple variant="outlined" density="comfortable"
                                :items="['Suporte', 'Desenvolvimento']" />
                        </v-col>

                        <v-col cols="12" md="4">
                            <v-select label="Prioridade" multiple variant="outlined" density="comfortable"
                                :items="['Alta', 'Média', 'Baixa']" />
                        </v-col>

                        <v-col cols="12" md="4">
                            <v-select label="Status" multiple variant="outlined" density="comfortable"
                                :items="['Aguardando Início', 'Em andamento', 'Concluído', 'Cancelado']" />
                        </v-col>

                        <!-- Botões -->
                        <v-col cols="12" class="d-flex justify-end gap-2">
                            <v-btn variant="text">Limpar</v-btn>
                            <v-btn color="primary">Buscar</v-btn>
                        </v-col>
                    </v-row>
                </v-form>
            </v-card>
        </v-container>

        <!-- Tabela -->
        <v-container fluid class="py-8 px-8">
            <v-card class="mx-auto pa-6">
                <v-card-title>Central de chamados</v-card-title>

                <div class="d-flex gap-2 mb-4">
                    <v-chip class="status-azul" label>
                        Em andamento
                    </v-chip>

                    <v-chip class="status-vermelho" label>
                        Concluído
                    </v-chip>
                </div>
                <v-table height="300px" fixed-header>

                    <thead>
                        <tr>
                            <th class="text-left">
                                Titulo
                            </th>
                            <th class="text-left">
                                Usuário Abertura
                            </th>
                            <th class="text-left">
                                Empresa
                            </th>
                            <th class="text-left">
                                Tipo
                            </th>
                            <th class="text-left">
                                Prioridade
                            </th>
                            <th></th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="chamado in objListaChamados" :class="BackgroundTable(chamado.Status)">
                            <td>{{ chamado.Titulo }}</td>
                            <td>{{ chamado.UsuarioAbertura }}</td>
                            <td>{{ chamado.Empresa }}</td>
                            <td>{{ chamado.TipoChamado }}</td>
                            <td>{{ chamado.Prioridade }}</td>
                            <td>
                                <v-btn density="compact" icon="mdi mdi-pencil-box-multiple-outline"></v-btn>
                            </td>
                        </tr>
                    </tbody>
                </v-table>
            </v-card>
        </v-container>
    </v-main>
</template>

<style>
.status-azul {
    background-color: #e3f2fd;
}

.status-vermelho {
    background-color: #ffebee;
}
</style>