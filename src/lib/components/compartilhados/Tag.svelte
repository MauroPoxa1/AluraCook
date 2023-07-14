<script lang="ts">
  export let ativa = false;
  export let tamanho: "md" | "lg" = "md";
  export let desabilitada = false;

  // function aoClicar() {
  //   ativa = !ativa;
  // }
</script>

<div class="tag {tamanho}"
class:ativa 
class:desabilitada
>
  <slot></slot>
</div>

<style>
  .tag {
    height: 48px;
    border-radius: 8px;
    padding: 1rem;
    text-align: center;
    color: var(--cor-texto-principal);
    background-color: var(--cinza);

    display: flex;
    justify-content: center;
    align-items: center;

    transition: 0.2s;
  }

  .ativa {
    color: var(--branco);
    background-color: var(--laranja);
  }

  .desabilitada{
    opacity: 0.8;
    cursor: default;
  }

  .lg {
    font-size: 1.25rem;
    padding: 1rem 1.5rem;
  }
</style>
