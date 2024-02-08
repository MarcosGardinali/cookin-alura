<script lang="ts">
import type IReceitas from '@/interfaces/IReceitas';
import CardReceita from './CardReceita.vue';
import type { PropType } from 'vue';

export default{
    props: {
        receitas: {type: Object}
    },
    components: { CardReceita }
}
</script>

<template>
    <p class="paragrafo-lg">Veja as opções de receitas que encontramos com os ingredientes que você tem aí!</p>
    
    <ul class="receitas">
        <li v-for="receita in receitas" :key="receita.nome">
            <CardReceita :receita="receita"/>
        </li>
    </ul>
</template>

<style scoped>
.receitas{
    margin-bottom: 1rem;
    display: flex;
    justify-content: center;
    gap: 1.5rem;
    flex-wrap: wrap;
}
</style>