<template>
  <q-card flat bordered class="view-card q-pa-md column justify-between" style="min-height: 120px;">
    <div class="relative-position full-width">
      <q-icon size="18px" class="absolute-top-right" color="green-9">
        <img :src="icon" alt="Ícone" width="18" height="18">
      </q-icon>

      <div class="column q-gutter-y-xs">
        <span class="text-body1" style="color: #1A3C2A;">
          {{ titulo }}
        </span>
        <div class="text-h4 text-bold" style="color: #1A3C2A;">
          {{ valor }}
        </div>
      </div>
    </div>

    <div class="row items-center q-gutter-x-xs text-caption self-start q-mt-sm" style="color: #2E7D32;">
      <q-icon size="12px" color="green-8">
        <img :src="estatistica > 0 ? '/icons/ArrowUpRight.svg' : '/icons/ArrowDownRight.svg'" alt="Seta" width="12"
          height="12"> </q-icon>
      <span class="text-weight-medium" :class="estatistica < 0 ? 'text-negative' : ''"
        :style="estatistica >= 0 ? 'color: #1A3C2A' : ''">{{ estatistica }} vs. semana passada</span>
    </div>
  </q-card>
</template>

<script setup lang="ts">

defineProps({
  titulo: { type: String, default: '' },
  icon: { type: String, default: '' },
  valor: { type: Number, default: 0 },
  estatistica: { type: Number, default: 0 }
})

</script>

<style scoped lang="sass">

$cor-fundo: #FAF8F5
.view-card
  width: 100%
  height: 150px
  max-width: 300px
  background-color: $cor-fundo
  border-radius: 10px

</style>
