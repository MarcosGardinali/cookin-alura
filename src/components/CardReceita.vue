<script lang="ts">
import type IReceitas from '@/interfaces/IReceitas';
import type { PropType } from 'vue';

export default{
    props: {
        receita: { type: Object as PropType<IReceitas>, required: true },
    }
}
</script>

<template>
    <article class="receita">
        <header class="receita__cabecalho">
            <img :src="`/imagens/receitas/${receita.imagem}`" alt="" class="receita__imagem">

            <h2 class="paragrafo-lg receita__nome">{{ receita.nome }}</h2>
        </header>

        <ul class="receita__ingredientes">
            <li v-for="ingrediente in receita.ingredientes" :key="ingrediente">
                {{ ingrediente }}
            </li>
        </ul>    
        
    </article>
</template>

<style scoped>
.receita {
    width: 19.5rem;
    padding: 1rem;
    border-radius: 1rem;
    background: var(--branco, #FFF);
    box-shadow: 4px 4px 10px 0px rgba(68, 68, 68, 0.05);
    height: 100%;

    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 2rem;
}

.receita__cabecalho {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.5rem;
}

.receita__imagem {
    width: 100%;
    border-radius: 1rem;
}

.receita__nome {
    text-align: center;
    color: var(--verde-medio, #3D6D4A);
    font-weight: 700;
}

.receita__ingredientes {
    display: flex;
    justify-content: center;
    gap: 0.5rem;
    flex-wrap: wrap;
}
</style>