<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="q-pa-sm">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title> BiblioSystem - Gestão de acervo </q-toolbar-title>

      </q-toolbar>
    </q-header>

    <q-drawer style="background-color: #F5F0E9;" v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <div class="q-pa-sm row justify-center items-center">
          <q-img :src="logo" style="width: 50px;" contain />
          <q-item-label header class="text-h6 q-border-bottom q-pb-sm">BiblioSystem</q-item-label>
        </div>
        <q-separator />


        <EssentialLink
          v-for="link in linksList"
          :key="link.label"
          v-bind="link"
          class="q-pa-md"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">

import { useRouter } from 'vue-router'

import logo from '@/assets/logo-bibliosystem.png'
import { ref } from "vue";
import EssentialLink, {
  type EssentialLinkProps
} from "@/components/EssentialLink.vue";

const router = useRouter()
router.push('/dashboard/Dashboard')

const linksList: EssentialLinkProps[] = [
  {
    label: "Dashboard",
    caption: "Dashboard",
    icon: "dashboard",
    link: "/dashboard/Dashboard"
  },
  {
    label: "Acervo",
    caption: "Acervo",
    icon: "book",
    link: "/acervo/AcervoList"
  },
  {
    label: "Empréstimo",
    caption: "Empréstimo",
    icon: "library_add",
    link: "/emprestimo/EmprestimoList"
  },
  {
    label: "Usuários",
    caption: "Usuários",
    icon: "person",
    link: "/usuario/UsuarioList"
  },
  {
    label: "Relatórios",
    caption: "Relatórios",
    icon: "analytics",
    link: "/relatorio/Relatorio"
  },
];

const leftDrawerOpen = ref(false);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}
</script>
