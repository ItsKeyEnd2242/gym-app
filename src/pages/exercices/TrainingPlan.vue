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
              <div class="q-pa-md q-gutter-sm">
                <p>Treino A</p>
    <q-btn label="Basic scroll" icon="add" color="primary" @click="funcaoAbreModal()" />

    <q-dialog v-model="basic" transition-show="rotate" transition-hide="rotate">
      <q-card>
        <q-card-section>
          <div class="text-h6">adicionar treino</div>
        </q-card-section>

        <q-card-section class="q-pt-none">
          flex-builder
        </q-card-section>

        <q-card-actions align="right">
          <q-btn flat label="cancelar" color="primary" v-close-popup />
          <q-btn flat label="adicionar" color="primary" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </div>                
            </q-card>
        </div>
    </q-page>
</template>

<style lang="scss" scoped>
/* AQUI VAI O ESTILO CSS DESTA PÁGINA EXCLUSIVAMENTE */

</style>

<script lang="ts">
import { ref } from 'vue';

import DialogNewTrainVue from './DialogNewTrain.vue';

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
        drawer: ref(false),
        basic: ref(false)
      }
    },
    methods: {
      // FUNÇÕES/MÉTODOS
      funcaoAbreModal () {
        this.ensinandoParametrosEmFuncoes('pedro é foda', 333, { 'variavel1': 'Valor 1', 'variavel2': 'Valor 2' });

        const cadastroCliente = {
          nome: 'Pedro Barbosa',
          idade: 17,
          endereco: 'ahhahahahahahahahah',
          cpf: '000.000.000-00',
          email: 'asusahsuhsuh@gmail.com'
        };

        this.novoCliente(cadastroCliente)

        this.$q
          .dialog({
            component: DialogNewTrainVue,
            persistent: true,
            cancel: true,
            // componentProps: {
            //   countries: product.countries
            // }
          })
          .onOk((novoTreino: any) => {
            console.log('novo treino: ', novoTreino)
          })
      },
      ensinandoParametrosEmFuncoes(parametro1: string, parametro2: number, parametro3: any) {
        console.log('parametro1: ', parametro1)
        console.log('parametro2: ', parametro2)
        console.log('parametro3: ', parametro3)
      },
      novoCliente (cliente: any) {
        if (cliente.nome === null) return false;
        else {
          console.log('cliente ok')
        }
      } 
      /**
       * 
       funcao onOk(novoTreino = 'parametro') {
        
       }
       */
    },
    computed: {
      // FUNÇÕES COMPUTADAS (FICAM EM CACHE NO NAVEGADOR PARA MELHORAR A PERFORMANCE)
    },
  }
  </script>
