<template>
    <!-- AQUI VAI OS COMPONENTES HTML -->
</template>

<style lang="scss" scoped>
 /* AQUI VAI O ESTILO CSS DESTA PÁGINA EXCLUSIVAMENTE */
</style>

<script lang="ts">
import { defineComponent, ref } from 'vue';

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
            variable: ref()
        }
    },
    methods: {
        // FUNÇÕES/MÉTODOS
    },
    computed: {
        // FUNÇÕES COMPUTADAS (FICAM EM CACHE NO NAVEGADOR PARA MELHORAR A PERFORMANCE)
    }
}
</script>