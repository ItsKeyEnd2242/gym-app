<template>
    <q-dialog v-model="confirm" persistent ref="dialog">
      <q-stepper v-model="step" vertical color="primary" animated>
        <q-step
          push
          :name="1"
          :title="tituloStepUm"
          icon="settings"
          :done="step > 1"
        >
          <div class="q-gutter-md bg-white">
            <q-input rounded outlined v-model="title" label="Insira o nome do seu exercício" maxlength="100"/>
  
            <q-card>
              <q-editor
                toolbar-push
                v-model="description"
                min-height="250px"
                min-width="550px"
                :toolbar="[
                  ['bold', 'italic', 'strike', 'underline'],
                  ['token', 'hr', 'link'],
                  ['quote', 'unordered', 'ordered', 'outdent', 'indent'],
                  ['undo', 'redo'],
                ]"
              />
            </q-card>
  
            <q-checkbox v-model="hasVideo" label="Deseja trocar o treino a cada 30 dias?" />
            <q-input rounded outlined v-if="hasVideo" v-model="videoUrl" label="Digite o seu próximo objetivo de treino"/>
          </div>
  
          <q-stepper-navigation>
            <q-btn push rounded class="bg-primary text-white" label="Clique para salvar" @click="onFinishClick()"/>
            <!-- Passo 3: utilizar o component no html -->
            <button-return @click="onExitClick()"/>
          </q-stepper-navigation>
        </q-step>
      </q-stepper>
    </q-dialog>
  </template>
  
<script lang="ts">
  import { ref } from 'vue'
  import { useDialogPluginComponent } from 'quasar'

  // Passo 1: Importar o component que você criou/custumizou
  import ButtonReturn from 'src/components/ButtonReturn.vue'
  
  export default {
    name: 'DialogNewTrain',
    components: {
        // Passo 2: dizer para o app, que você vai utilizar esse componente
        ButtonReturn
    },
    data () {
      return {
        confirm: false,
        step: ref(1),
        title: ref(''),
        description: ref(''),
        hasVideo: ref(false),
        videoUrl: ref(''),
        tituloStepUm: ref('Preencha as informações do seu treino')
      }
    },
    emits: {
      ...useDialogPluginComponent.emits
    },
    methods: {
      onFinishClick () {
        if (!this.validateBeforeExit()) {
            //TODO: CRIAR MENSAGEM DE NOTIFICAÇÃO PARA PREENCHER TODOS OS CAMPOS OBRIGATÓRIOS
        }
        else {
          const newTipObj = {
            title: this.title,
            description: this.purifiedDescription(),
            availableAllModules: true,
            hasVideo: this.hasVideo,
            videoUrl: this.videoUrl,
            type: 'ADWORDS'
          }
          this.$emit('ok', newTipObj)
          this.$emit('hide') //Fecha a modal
        }
      },
      validateBeforeExit () {
        // Valida campos nulos
        if (!this.title) return false
        else if (!this.description) return false
        else if (this.hasVideo) {
          if (!this.videoUrl) return false
        }
        return true
      },
      purifiedDescription () {
        return this.description
          .replace(/<div><br><\/div>/g, '<br>')
          .replace(/<\/div><div>/g, '')
          .replace(/<\/div>/g, '')
          .replace(/&gt;/g, '>')
          .replace(/&lt;/g, '<')
      },
      onExitClick () {
        (this as any).$refs.dialog.hide()
      },
      show () {
        (this as any).$refs.dialog.show()
      }
    }
  }
  </script>
  