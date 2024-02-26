<!-- eslint-disable vue/no-use-v-if-with-v-for -->
<!-- AQUI VAI OS COMPONENTES HTML -->
<template>
    <q-page>
      <br>
      <rounded-input v-model="textToSearch" :icon="'search'" style="max-width: 350px" />
      <br>
      <button-add @click="onNewTrainRegistrationClick"/>

      <div class="q-pa-md row justify-center q-gutter-sm" v-if="listUserTrainings.length > 0">
        <q-intersection
          v-for="(t, index) in computedUserTrainingList"
          :key="index"
          class="example-item"
        >
          <q-card flat bordered class="custom-card">
            <q-card-section>
              <div class="text-h6">Treino {{ t.title }}</div>
              <div class="text-subtitle2">Descrição {{ t.description }}</div>

              <div v-if="t.exercices.length > 0" v-for="(e, index) in t.exercises" :key="index">
                
              </div>
            </q-card-section>
            <q-separator />
            <q-card-actions align="center">
              <q-btn push rounded label="Excluir" icon="mdi-close" class="bg-white text-primary" />
              <q-btn @click="onNewTrainRegistrationClick" push rounded label="Editar" icon="edit" class="bg-primary text-white" />
            </q-card-actions>
          </q-card>
        </q-intersection>
      </div>

        <!-- <q-btn push rounded label="CLIQUE AQUI" icon="add" @click="onClickButton"/>
        <q-input
            class="text-white"
            rounded outlined
            v-model="currentUserName"
            type="text"
            label="INFORME O SEU NOME DESGRAÇADO"
        /> -->
        <!-- <div class="q-pa-md">
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
        </div> -->
    </q-page>
</template>

<style lang="sass" scoped>
.custom-card
  border-radius: 10px

</style>

<script lang="ts">
import { ref } from 'vue';

import DialogNewTrainVue from './DialogNewTrain.vue';
import RoundedInput from 'src/components/RoundedInput.vue';
import ButtonAdd from 'src/components/ButtonAdd.vue'

  export default {
    components: {
      //BOTÕES/COMPONENTES CUSTOMIZADOS
      RoundedInput,
      ButtonAdd
    },
    props: {
      //SUAS PROPRIEDADES

    },
    data () {
      // Declara a variável como tipo 'array' e inicializa ela para evitar o erro: Argument of type 'any' is not assignable to parameter of type 'never'.ts(2345)
      const listUserTrainings: [] = [
        { title: 'teste 1', description: 'shaushau', exercices: [ { series: 3, name: 'Pull down', time: '30s', carga: '10kg' }] },
        { title: 'teste 2', description: 'shaushau', exercices: [ { series: 3, name: 'Pull down', time: '30s', carga: '10kg' }] },
        { title: 'teste 3', description: 'shaushau', exercices: [ { series: 3, name: 'Pull down', time: '30s', carga: '10kg' }] },
        { title: 'teste 4', description: 'shaushau', exercices: [ { series: 3, name: 'Pull down', time: '30s', carga: '10kg' }] },
        { title: 'teste 5', description: 'shaushau', exercices: [ { series: 3, name: 'Pull down', time: '30s', carga: '10kg' }] },
        { title: 'teste 6', description: 'shaushau', exercices: [ { series: 3, name: 'Pull down', time: '30s', carga: '10kg' }] },
        { title: 'teste 7', description: 'shaushau', exercices: [ { series: 3, name: 'Pull down', time: '30s', carga: '10kg' }] },
        { title: 'teste 8', description: 'shaushau', exercices: [ { series: 3, name: 'Pull down', time: '30s', carga: '10kg' }] },
      ]

      // INICIALIZAÇÃO DESTA PÁGINA
      return {
        variable: ref(),
        drawer: ref(false),
        basic: ref(false),
        textToSearch: ref(''),
        listUserTrainings
      }
    },
    methods: {
      // FUNÇÕES/MÉTODOS
      onNewTrainRegistrationClick () {
        this.$q
          .dialog({
            component: DialogNewTrainVue,
            persistent: true,
            cancel: true,
            // componentProps: {
            //   countries: product.countries
            // }
          })
          .onOk((newTraining) => {
            if (newTraining) {
              this.listUserTrainings.push(newTraining)
            }
          })
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
      computedUserTrainingList () {
        return this.listUserTrainings
      }
    },
  }
  </script>
