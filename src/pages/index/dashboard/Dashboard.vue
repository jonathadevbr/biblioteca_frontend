<template>
  <q-page class="q-pt-xl" style="padding-left: 200px;">
    <div class="text-h4 q-mb-none titulo-dasboard">Dashboard</div>

    <span class="q-mt-xs text-body1 block">Aqui está um resumo do acervo e movimentações de hoje.</span>

    <div class="q-pt-xl row items-start q-gutter-md">
      <ViewCard
      v-for="card in cards"
      :key="card.titulo"
      :titulo="card.titulo"
      :valor="card.valor"
      :estatistica="card.estatistica"
      :icon="card.icon"
      />
    </div>

    <div class="q-pt-xl" style="width: 1000px;">
      <q-table title="Empréstimos recentes" :rows="rows" :columns="columns" row-key="name" class="my-q-table" />
    </div>
  </q-page>
</template>

<script setup lang="ts">
import ViewCard from '@/components/ViewCard.vue';
import { QTableColumn } from 'quasar'

import AlertTriangle from '@/assets/AlertTriangle.png'
import BookOpen from '@/assets/BookOpen.png'
import Users from '@/assets/Users.png'
import BookMarked from '@/assets/BookMarked.png'

const cards = [
  { titulo: 'Livros no acervo', valor: 4.827, estatistica: 2.1, icon: BookOpen },
  { titulo: 'Emprestimos ativos', valor: 312, estatistica: 18, icon: BookMarked },
  { titulo: 'Usuários cadastrados', valor: 1.246, estatistica: 34, icon: Users },
  { titulo: 'Atrasos', valor: 27, estatistica: -4, icon: AlertTriangle },
]

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
  border-radius: 10px

.my-q-table
  border-radius: 10px
</style>
