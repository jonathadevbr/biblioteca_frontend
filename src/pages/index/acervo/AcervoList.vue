<template>
  <q-page class="q-pt-xl" style="padding-left: 200px;">
    <div class="text-h4 q-mb-none titulo-acervo">Acervo</div>

    <span class="q-mt-xs text-body1 block">Gerencie títulos, categorias e autores da biblioteca.</span>

    <div class="q-pa-md">
      <div class="q-gutter-y-md" style="max-width: 600px">
        <q-card>
          <q-tabs v-model="tab" dense class="text-grey" active-color="primary" indicator-color="primary" align="justify"
            narrow-indicator>
            <q-tab name="livros" label="Livros" />
            <q-tab name="categorias" label="Categorias" />
            <q-tab name="autores" label="Autores" />
          </q-tabs>

          <q-separator />

          <q-tab-panels v-model="tab" animated>
            <q-tab-panel name="livros">
              <LivroList />
            </q-tab-panel>

            <q-tab-panel name="categorias">
              <CategoriaList />
            </q-tab-panel>

            <q-tab-panel name="autores">
              <AutorList />
            </q-tab-panel>
          </q-tab-panels>
        </q-card>
      </div>
    </div>
  </q-page>
</template>

<script setup lang="ts">
import AutorList from '@/components/acervo/autor/AutorList.vue';
import CategoriaList from '@/components/acervo/categoria/CategoriaList.vue';
import LivroList from '@/components/acervo/livro/LivroList.vue';
import { ref } from 'vue'

const tab = ref('livros')
</script>

<style scoped lang="sass">
.titulo-acervo
  font-family: 'Playfair Display', 'Times New Roman', serif;
  color: #1a2e24;
  font-weight: 600;
</style>
