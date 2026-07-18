<template>
  <q-page class="q-pt-xl" style="padding-left: 200px;">
    <div class="text-h4 q-mb-none titulo-dasboard">Dashboard</div>

    <span class="q-mt-xs text-body1 block">Aqui está um resumo do acervo e movimentações de hoje.</span>

    <div class="q-pt-xl row items-start q-gutter-md">
      <q-card class="my-card q-pa-lg column justify-between" style="min-height: 160px; border-radius: 12px;">
        <div class="relative-position full-width">
          <q-icon size="20px" class="absolute-top-right" color="green-9">
            <img src="/src/assets/BookOpen.svg" alt="Livro">
          </q-icon>

          <div class="column q-gutter-y-sm">
            <span class="text-body1 text-grey-7">Livros no acervo</span>
            <div class="text-h4 text-bold" style="color: #1B4332;">
              {{ livros_acervo }}
            </div>
          </div>
        </div>

        <div class="row items-center q-gutter-x-sm text-caption self-start q-mt-md" style="color: #2E7D32;">
          <q-icon size="14px" color="green-8">
            <img src="/src/assets/ArrowUpRight.svg" alt="Seta">
          </q-icon>
          <span class="text-weight-medium">+2,1% vs. semana passada</span>
        </div>
      </q-card>

      <q-card class="my-card q-pa-lg column justify-between" style="min-height: 160px; border-radius: 12px;">
        <div class="relative-position full-width">
          <q-icon size="20px" class="absolute-top-right" color="green-9">
            <img src="/src/assets/BookMarked.svg" alt="Livro">
          </q-icon>

          <div class="column q-gutter-y-sm">
            <span class="text-body1 text-grey-7">Empréstimos ativos</span>
            <div class="text-h4 text-bold" style="color: #1B4332;">
              {{ emprestimos_ativos }}
            </div>
          </div>
        </div>

        <div class="row items-center q-gutter-x-sm text-caption self-start q-mt-md" style="color: #2E7D32;">
          <q-icon size="14px" color="green-8">
            <img src="/src/assets/ArrowUpRight.svg" alt="Seta">
          </q-icon>
          <span class="text-weight-medium">+18 vs. semana passada</span>
        </div>
      </q-card>

      <q-card class="my-card q-pa-lg column justify-between" style="min-height: 160px; border-radius: 12px;">
        <div class="relative-position full-width">
          <q-icon size="20px" class="absolute-top-right" color="green-9">
            <img src="/src/assets/Users.svg" alt="Livro">
          </q-icon>

          <div class="column q-gutter-y-sm">
            <span class="text-body1 text-grey-7">Usuários cadastrados</span>
            <div class="text-h4 text-bold" style="color: #1B4332;">
              {{ usuarios_cadastrados }}
            </div>
          </div>
        </div>

        <div class="row items-center q-gutter-x-sm text-caption self-start q-mt-md" style="color: #2E7D32;">
          <q-icon size="14px" color="green-8">
            <img src="/src/assets/ArrowUpRight.svg" alt="Seta">
          </q-icon>
          <span class="text-weight-medium">+34 vs. semana passada</span>
        </div>
      </q-card>

      <q-card class="my-card q-pa-lg column justify-between" style="min-height: 160px; border-radius: 12px;">
        <div class="relative-position full-width">
          <q-icon size="20px" class="absolute-top-right" color="green-9">
            <img src="/src/assets/AlertTriangle.svg" alt="Livro">
          </q-icon>

          <div class="column q-gutter-y-sm">
            <span class="text-body1 text-grey-7">Atrasos</span>
            <div class="text-h4 text-bold" style="color: #1B4332;">
              {{ atrasos }}
            </div>
          </div>
        </div>

        <div class="row items-center q-gutter-x-sm text-caption self-start q-mt-md" style="color: #2E7D32;">
          <q-icon size="14px" color="green-8">
            <img src="/src/assets/ArrowDownRight.svg" alt="Seta">
          </q-icon>
          <span class="text-weight-medium">-4 vs. semana passada</span>
        </div>
      </q-card>
    </div>

    <div class="q-pt-xl" style="width: 1000px;">
      <q-table title="Empréstimos recentes" :rows="rows" :columns="columns" row-key="name" class="my-q-table" />
    </div>
  </q-page>
</template>

<script setup lang="ts">
import { QTableColumn } from 'quasar'

const lorem = '...'
let livros_acervo = 4.827;
let emprestimos_ativos = 312;
let usuarios_cadastrados = 1.246;
let atrasos = 27;

interface RowData {
  emprestimo: string
  data_devolucao: string
  status: boolean
}

const columns: QTableColumn<RowData>[] = [
  {
    name: 'emprestimos',
    required: true,
    align: 'left',
    label: '',
    field: (row: RowData) => row.emprestimo,
    format: (val: string) => `${val}`,
    sortable: true
  },
  {
    name: 'data_devolucao',
    label: '',
    align: 'center',
    field: 'data_devolucao',
    sortable: true
  },
  {
    name: 'status',
    label: '',
    field: 'status',
    sortable: true
  },
]

const rows: RowData[] = [
  {
    emprestimo: 'Dom Casmurro',
    data_devolucao: '08/07/2026',
    status: true
  },
  {
    emprestimo: 'Sapiens',
    data_devolucao: '15/07/2026',
    status: true
  },
  {
    emprestimo: 'O Cortiço',
    data_devolucao: '31/07/2026',
    status: true
  },
  {
    emprestimo: '1984',
    data_devolucao: '22/07/2026',
    status: true
  },
  {
    emprestimo: 'A Hora da Estrela',
    data_devolucao: '28/07/2026',
    status: true
  },
]
</script>

<style scoped lang="sass">
.titulo-dasboard
  font-family: 'Playfair Display', 'Times New Roman', serif
  color: #1a2e24
  font-weight: 600

$cor-fundo: #FAF8F5

.my-card
  width: 100%
  height: 150px
  max-width: 350px
  background-color: $cor-fundo
  border-radius: 10px

.my-q-table
  background-color: $cor-fundo
  border-radius: 10px
</style>
