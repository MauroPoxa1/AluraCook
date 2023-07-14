<script lang="ts">
  import Tag from "../../compartilhados/Tag.svelte";
  import { minhaLista } from "$lib/stores/minhaLista";
  import MeuIgrediente from "./MeuIgrediente.svelte";
  export let ingredientes: string[];

</script>

<saction class="minha-lista">
  <h2>Sua lista:</h2>

  <ul class="meus-ingredientes">
    {#each $minhaLista as ingrediente (ingrediente)}
    <li>
      <MeuIgrediente {ingrediente}/>
    </li>
    {/each}
  </ul>
</saction>

<style>
  .minha-lista {
    padding-bottom: 1.625rem;
  }

  .minha-lista > h2 {
    font-size: 1.5rem;
    color: var(--laranja);
    margin-bottom: 1.5rem;
    line-height: 2rem;
    font-weight: 700;
  }

  .meus-ingredientes {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 0.75rem 1.875rem;
  }
</style>
