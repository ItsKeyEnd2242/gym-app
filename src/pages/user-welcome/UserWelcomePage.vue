<!-- AQUI VAI OS COMPONENTES HTML -->
<template>
  <div class="q-pa-md">
    <q-layout view="lHh Lpr lff" container style="height: 90vh" class="shadow-2 rounded-borders">
      <q-header elevated class="bg-cyan-8">
        <q-toolbar>
          <q-btn flat @click="drawer = !drawer" round dense icon="menu" />
          <q-toolbar-title>Menu</q-toolbar-title>
        </q-toolbar>

      </q-header>

      <q-drawer v-model="drawer" show-if-above :width="250" :breakpoint="0" :height="250" bordered>
        <q-list>

        <q-expansion-item
        expand-separator
        icon="mail"
        label="Inbox"
        caption="5 unread emails"
        default-opened>
        <q-item class="bg-primary text-white" clickable v-ripple>
            <q-item-section avatar><q-icon name="mdi-dumbbell"/></q-item-section>
            <q-item-section>Treinos</q-item-section>
          </q-item>
          <q-item class="bg-accent text-white" clickable v-ripple>
            <q-item-section avatar><q-icon name="mdi-dumbbell"/></q-item-section>
            <q-item-section>Treinos</q-item-section>
          </q-item>
        </q-expansion-item>
        
        <q-fab color="secondary" push icon="keyboard_arrow_right" direction="right">
        <q-fab-action color="primary" @click="onClick" icon="mail" />
        <q-fab-action color="accent" @click="onClick" icon="alarm" />
      </q-fab>
      </q-list>
      </q-drawer>
    </q-layout>
  </div>
  </template>

<style lang="scss" scoped>
/* AQUI VAI O ESTILO CSS DESTA PÁGINA EXCLUSIVAMENTE */

</style>

<script lang="ts">
import { ref } from 'vue';

export default {
  components: {
    //BOTÕES/COMPONENTES CUSTOMIZADOS  
  },
  props: {
    //SUAS PROPRIEDADES
  },
  data () {
    // INICIALIZAÇÃO DESTA PÁGINA
    return {
      variable: ref(),
      drawer: ref(false)
    }
  },
  methods: {
    // FUNÇÕES/MÉTODOS
  },
  computed: {
    // FUNÇÕES COMPUTADAS (FICAM EM CACHE NO NAVEGADOR PARA MELHORAR A PERFORMANCE)
  },
}
</script>