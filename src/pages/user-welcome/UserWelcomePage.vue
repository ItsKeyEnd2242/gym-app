<!-- AQUI VAI OS COMPONENTES HTML -->
<template>
  <q-layout view="lHh Lpr lff" container style="height: 90vh" class="shadow-2 rounded-borders">
    <q-header elevated class="bg-cyan-8">
      <q-toolbar>
        <q-btn flat @click="drawer = !drawer" round dense icon="menu" />
        <q-toolbar-title>Menu</q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="drawer" show-if-above :width="250" :breakpoint="0" :height="250" bordered>
      <q-list>
        <!-- q-expansion treinos -->
        <q-expansion-item
          expand-separator
          icon="mdi-human" 
          label="Seu treino"
          default-opened
        >
          <q-item class="bg-primary text-white" clickable v-ripple to="/exercises">
            <q-item-section avatar><q-icon name="mdi-dumbbell"/></q-item-section>
            <q-item-section>Exercicios e divisões</q-item-section>
          </q-item>
          <q-item class="bg-accent text-white" clickable v-ripple>
            <q-item-section avatar><q-icon name="mdi-food-apple"/></q-item-section>
            <q-item-section>Dieta</q-item-section>
          </q-item>
        </q-expansion-item>
        <!-- q-expansion de configurações -->
        <q-expansion-item
          expand-separator
          icon="mdi-cog-outline"
          label="Configuração"
          default-opened
        >
        <!-- q-expansion opções dentro de configurações -->
        <q-expansion-item
          expand-separator
          icon=""
          label="Opções"
          default-opened
        >
          <q-item class="bg-light-blue text-black" clickable v-ripple>
            <q-item-section avatar><q-icon name="mdi-phone-outline"/></q-item-section>
            <q-item-section>Suporte</q-item-section>
          </q-item>
          <q-item class="bg-accent text-white" clickable v-ripple>
            <q-item-section avatar><q-icon name="mdi-account-cog"/></q-item-section>
            <q-item-section>Conta</q-item-section>
          </q-item>
        </q-expansion-item>
          <q-item class="bg-red text-white" clickable v-ripple>
            <q-item-section avatar><q-icon name="mdi-logout"/></q-item-section>
            <q-item-section>Sair da conta</q-item-section>
          </q-item>
        </q-expansion-item>      
      </q-list>
    </q-drawer>

    <q-page-container> <!-- Container de novas páginas -->
      <router-view /> <!-- Dentro do container, nós vamos criar um atalho para as rotas -->
    </q-page-container>
  </q-layout>

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