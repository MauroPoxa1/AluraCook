<script lang="ts">
    import Card from "$lib/components/compartilhados/Card.svelte";
     import type ICategorias from "$lib/interfaces/ICategorias";
     import IngredienteSelecionavel from "./IngredienteSelecionavel.svelte";


      export let categoria: ICategorias;
</script>

<Card>
    <div class="categoria-container">
        <img 
        src="../icones/categorias_ingredientes/{categoria.imagem}" 
        alt="{categoria.nome}"
        class="categoria-imagem"
        >
        <h3 class="categoria-nome">{categoria.nome}</h3>
        <ul class="ingredientes">
            {#each categoria.ingredientes as ingrediente (ingrediente)}
                <li>
                <IngredienteSelecionavel 
                ingrediente={ingrediente}
                />
                </li>
            {/each}
        </ul>
    </div>
</Card>

<style>
    .categoria-container {

        padding: 0.75rem 0.5rem;
    }

    .categoria-imagem {
        margin-bottom: 0.5rem;
    }

    .categoria-nome {
        font-size: 1.125rem;
        color: var(--verde);
        margin-bottom: 0.875rem;
    }

    .ingredientes {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        gap: 0.75rem 1rem;
    }
</style>