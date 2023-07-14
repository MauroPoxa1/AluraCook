<script lang="ts">
  import Titulo from "$lib/components/compartilhados/Titulo.svelte";
  import  categorias from "$lib/json/categorias.json";
  import Categorias from "$lib/components/pagina/index/Categorias.svelte";


  import { minhaLista } from "$lib/stores/minhaLista";
  import { beforeNavigate } from "$app/navigation";
  import TagLink from "$lib/components/compartilhados/TagLink.svelte";

  $: listaVasia = $minhaLista.length === 0;
  beforeNavigate((navigation)=> {
    // console.log( navigation.to?.url.pathname)
    listaVasia && navigation.to?.url.pathname==='/receitas' ? navigation.cancel() : '';
  });

//  function adicionarIngrediente(evento: CustomEvent<string>){
//   const ingrediente = evento.detail;
//   $minhaLista = [...$minhaLista, ingrediente]
//  } 

//  function removerIngradiente(evento: CustomEvent<string>){
//   const ingrediente = evento.detail;
//   $minhaLista = $minhaLista.filter(
//     (item) => item !== ingrediente
//   );
//  }
</script>

<svelte:head>
  <title>Alura Cook</title>
</svelte:head>


    <main>
      <Titulo tag='h1'>Ingradientes</Titulo>
      <div class="info">
        <p>
          Selecione abaixo os ingredientes que você deseja usar nesta refeição:
        </p>
        <p>
          *Atenção: consideramos que você tenha em casa sal, pimenta e água.
        </p>
      </div>

      <ul class="categorias">
        {#each categorias as categoria (categoria.nome)}
            <li>
                <Categorias 
                {categoria}
                />
            </li>
        {/each}
      </ul>
      <div class="buscar-receitas">
        <TagLink href="/receitas" desabilitada={listaVasia} >
            Buscar Receitas!
         </TagLink>
      </div>
    </main>



<style>

  .info {
    margin-bottom: 3.375rem;
  }
  .info > p {
    line-height: 2rem;
  }

  .categorias {
    margin-bottom: 4.6875rem;

    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 1.5rem;
  }

  .buscar-receitas {
    display: flex;
    justify-content: center;
  }
</style>
