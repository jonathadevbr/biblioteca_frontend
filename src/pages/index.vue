<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title> BiblioSystem </q-toolbar-title>

      </q-toolbar>
    </q-header>

    <q-drawer style="background-color: #F5F0E9;" v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <div class="row">
          <q-img :src="logo" style="width: 100px;" contain />
          <q-item-label header class="text-h6"> BiblioSystem </q-item-label>
        </div>


        <EssentialLink
          v-for="link in linksList"
          :key="link.label"
          v-bind="link"
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
    caption: "quasar.dev",
    icon: "school",
    link: "https://quasar.dev"
  },
  {
    label: "Acervo",
    caption: "github.com/quasarframework",
    icon: "code",
    link: "https://github.com/quasarframework"
  },
  {
    label: "Empréstimo",
    caption: "chat.quasar.dev",
    icon: "chat",
    link: "https://chat.quasar.dev"
  },
  {
    label: "Leitores",
    caption: "forum.quasar.dev",
    icon: "record_voice_over",
    link: "https://forum.quasar.dev"
  },
  {
    label: "Relatórios",
    caption: "@quasarframework",
    icon: "rss_feed",
    link: "https://twitter.quasar.dev"
  },
];

const leftDrawerOpen = ref(false);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}
</script>
