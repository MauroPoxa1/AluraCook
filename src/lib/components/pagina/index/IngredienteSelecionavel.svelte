<script lang="ts">
  import { minhaLista } from "$lib/stores/minhaLista";
  import Tag from "../../compartilhados/Tag.svelte";
  export let ingrediente: string;

  $: selecionado = $minhaLista.includes(ingrediente);

function aoClicar(){
    // selecionado = !selecionado;

    if (!selecionado){
        // // dispatch para adicionar ingradientes
        // //  $minhaLista = [...$minhaLista, ingrediente]
        //  minhaLista.update((valorAtual) => [...valorAtual, ingrediente]);

    minhaLista.adicionarIngrediente(ingrediente);
    }else {
        // //  $minhaLista = $minhaLista.filter(
        // //  (item) => item !== ingrediente);
        //  minhaLista.update((valorAtual) => valorAtual.filter( 
        //     (item) => item !== ingrediente)
        //     );
        minhaLista.removerIngrediente(ingrediente);
    }
}
</script>

<button on:click={aoClicar}>
<Tag ativa={selecionado}>  {ingrediente}</Tag>
</button>

<style>
    button{
        cursor: pointer;
    }
</style>