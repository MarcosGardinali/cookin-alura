<script lang="ts">
import Tag from './Tag.vue';

export default {
    props: {
        ingredientes: { type: Object, required: true }
    },
    components: { Tag }
}
</script>

<template>
    <section>
        <span class="subtitulo-lg sua-lista-texto">
            Sua Lista:
        </span>
        <ul v-if="ingredientes.length" class="ingredientes-sua-lista"> <!--v-if serve para colocar uma condição para determinado elemento ser renderizado-->
            <li v-for="ingrediente in ingredientes" :key="ingrediente"> <!--O v-for precorre a lista passada para ele e renderiza os elementos da lista na tag | O v-bind:key-"" ou :key="" serve para vincular o próprio ingrediente como chave do elemento dele mesmo-->
                <Tag :texto="ingrediente" ativa />
            </li>
        </ul>

        <p v-else class="paragrafo lista-vazia"> <!--v-else deve ser colocado no elemento seguinte de um que possui v-if para ser renderizado de acordo com a condição anterios não ser atendida-->
            <img src="../assets/images/icones/lista-vazia.svg" alt="Ícone de pesquisa">
            Sua lista está vazia selecione ingredientes para iniciar
        </p>
    </section>
</template>

<style scoped>
.sua-lista-texto {
    color: var(--coral, #F0633C);
    display: block;
    text-align: center;
    margin-bottom: 1.5rem;
}

.ingredientes-sua-lista {
    display: flex;
    justify-content: center;
    gap: 1rem 1.5rem;
    flex-wrap: wrap;
}

.lista-vazia {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    gap: 0.25rem;

    color: var(--coral, #F0633C);
    text-align: center;
}
</style>