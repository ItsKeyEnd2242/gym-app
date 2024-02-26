<template>
    <q-input rounded outlined label="Digite para pesquisar" type="text" :icon="icon"/>
</template>

<script lang="ts">
export default {
    name: 'RoundedInput',
    props: {
        icon: {
            default: 'add',
            required: false
        }
    }
}
</script>