<script lang="ts">
import Tag from './Tag.vue';

export default {
    components: { Tag },
    props: {
        ingrediente: { type: String, required: true }
    },
    data() {
        return {
            selecionado: false
        }
    },
    methods: {
        aoClicar() {
            this.selecionado = !this.selecionado

            if (this.selecionado) {
                this.$emit('adicionarIngrediente', this.ingrediente)//Está sendo criado um evento personalizado, onde a primeira informação é o nome e a segunda é o dado
            } else {
                this.$emit('removerIngrediente', this.ingrediente)
            }
        }
    },
    emits: ['adicionarIngrediente', 'removerIngrediente']

}
</script>

<template>
    <button class="ingrediente" v-on:click="aoClicar" :aria-pressed="selecionado">
        <!--No caso do v-on:click ele poderia ser resumido em @click-->
        <Tag :texto="ingrediente" :ativa="selecionado" />
    </button>
</template>


<style scoped>
.ingrediente {
    cursor: pointer;
}
</style>