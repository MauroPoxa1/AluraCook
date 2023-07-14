<script>
import Receita from "$lib/components/pagina/receitas/Receita.svelte";
import Titulo from "$lib/components/compartilhados/Titulo.svelte";
import receitas from "$lib/json/receitas.json";
import { minhaLista } from "$lib/stores/minhaLista";
  import TagLink from "$lib/components/compartilhados/TagLink.svelte";

$: receitasFiltradas = receitas.filter((receitas) => (
    receitas.ingredientes.every((ingradiente) => (
    $minhaLista.includes(ingradiente)
    ))
));

</script>
<svelte:head>
    <title>Alura Cook | Receitas</title>
</svelte:head>

<p>Aqui vem as receitas...</p>


<main>
    <Titulo tag="h1">Receitas</Titulo>

    <div class="info">
        <p class="verde">
            Resultados Encontrados: {receitasFiltradas.length}
        </p>
        {#if receitasFiltradas.length}
        <p>
            Veja as opções de receitas que encontramos com os ingredientes que você tem por aí!
        </p>
        {:else}
        <p>
            Não encontramos nenhuma receita com os seus ingredientes!
        </p>
        {/if}

        {#if receitasFiltradas.length}
        <ul class="receitas">
            {#each receitasFiltradas  as receita (receita.nome) }
            <il>
                <Receita {receita}/>
            </il>
            {/each}
        </ul>
        {/if}


        <div class="editar-lista">
            <TagLink href="/">
                Editar lista
             </TagLink>
        </div>

    </div>
</main>

<style>
    .info {
        margin-bottom: 3.375rem;
    }

    .info > p {
        line-height: 2rem;
    }

     .verde {
        color: var(--verde);
    }
    p:nth-child(2){
        margin-bottom: 3rem;
    }

    .receitas {
        text-align: start;
        margin-bottom: 3.75rem;

        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        gap: 1.5rem;
    }
    .editar-lista {
        display: flex;
        justify-content: center;
    }
</style>