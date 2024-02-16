<template>
  <q-btn label="text"> </q-btn>
</template>

<script lang="ts">
import { ref } from 'vue';

export default {
  components: {
    //BOTÕES/COMPONENTES CUSTOMIZADOS
  },
  props: {
    //SUAS PROPRIEDADES
  },
  data() {
    // INICIALIZAÇÃO DESTA PÁGINA
    return {
      variable: ref(),
      drawer: ref(false),
    };
  },
  methods: {
    // FUNÇÕES/MÉTODOS
  },
  computed: {
    // FUNÇÕES COMPUTADAS (FICAM EM CACHE NO NAVEGADOR PARA MELHORAR A PERFORMANCE)
  },
};
</script>
