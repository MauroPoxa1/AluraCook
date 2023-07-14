<script lang="ts">
  import Tag from "./Tag.svelte";

export let href: string;
export let desabilitada = false
</script>
<a 
{href}
>
  <Tag tamanho="lg" 
  {desabilitada}
  ativa={true}
  >
<slot/>
</Tag>
</a>