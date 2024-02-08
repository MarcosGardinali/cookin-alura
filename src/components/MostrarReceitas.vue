<script lang="ts">
import type IReceitas from '@/interfaces/IReceitas';
import ListaReceitas from './ListaReceitas.vue';
import { obterReceitas } from '@/http';
import BotaoPrincipal from './BotaoPrincipal.vue';
import type { PropType } from 'vue';
import { itensDeLista1EstaoEmLista2 } from '@/operacoes/listas';

export default {
    props: {
        ingredientes: { type: Array as PropType<string[]>, required: true }
    },
    data() {
        return {
            receitas: [] as IReceitas[]
        };
    },
    async created() {
        const receitasEncontradas = await obterReceitas();

        this.receitas = this.receitas.filter((receita) => {
            const possoFazerReceita = itensDeLista1EstaoEmLista2(receita.ingredientes, this.ingredientes);

            return possoFazerReceita
        });
    },
    components: { ListaReceitas, BotaoPrincipal },
    emits: ['SelecionarIngredientes']
}
</script>

<template>
    <h1 class="cabecalho titulo-ingredientes">Receitas</h1>
    <p class="paragrafo-lg instrucoes">Resultados encontrados <span>{{ receitas.length }}</span></p>

    <ListaReceitas v-if="receitas.length > 0" :receitas="receitas" />

    <img v-else src="../assets/images/sem-receitas.png" alt="Nenhuma Receita encontrada">

    <BotaoPrincipal :texto="'Editar'" @click="$emit('SelecionarIngredientes')" />
</template>

<style scoped></style>