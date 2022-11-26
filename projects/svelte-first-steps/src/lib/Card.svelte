<script>
  export let items;

  $: cardTotal = items.reduce((sum, curValue)=>{
    return sum + curValue.price;
  });
</script>

{#if DataTransferItemList.length === 0}
<p>No items in cart</p>
{:else}

<ul>
  {#each items as item}
    <li>{item.title} - {item.price}</li>
  {/each}
</ul>
{/if}
<h1>TOTAL: ${cardTotal}</h1>


<style>
  ul {
    list-style: none;
    margin: 1rem;
    padding: 0;
  }
  li {
    margin: 0.5rem 0;
    padding: 0.5rem;
    border: 1px solid #CCC;
  }
  h1 {
    font-size: 1.5rem;
  }
</style>