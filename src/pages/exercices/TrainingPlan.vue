<!-- AQUI VAI OS COMPONENTES HTML -->
<template>
    <q-page>
        <!-- <q-btn push rounded label="CLIQUE AQUI" icon="add" @click="onClickButton"/>
        <q-input
            class="text-white"
            rounded outlined
            v-model="currentUserName"
            type="text"
            label="INFORME O SEU NOME DESGRAÇADO"
        /> -->
        <div class="q-pa-md">
            <q-card class="" style="width: 300px; height: 150px;">
                <q-card-section>
                    TREINO A
                </q-card-section>
                <q-card-action>
                    <q-btn push rounded label="Excluir treino" icon="add" @click="onClickButton"/>
                    <q-btn push rounded label="Visualizar treino" class="bg-primary text-white" icon="add" @click="onClickButton"/>
                </q-card-action>
            </q-card>
        </div>
    </q-page>
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
      onClickButton () {
        console.log('dionei e o pedro vão mudar o mundo com esse projeto')
      }
    },
    computed: {
      // FUNÇÕES COMPUTADAS (FICAM EM CACHE NO NAVEGADOR PARA MELHORAR A PERFORMANCE)
    },
  }
  </script>