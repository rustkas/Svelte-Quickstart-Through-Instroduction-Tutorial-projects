<script>
  import Product from './lib/Product.svelte';
  import Button from './lib/Button.svelte';
  import Card from './lib/Card.svelte';

  let title = '';
  let price = 0;
  let description = '';
  let products = [];
  let cardItems = [];

  function setTitle(event) {
    title = event.target.value;
  }

  function createProduct() {
    const newProduct = {
      title,
      price,
      description,
    };
    products = products.concat(newProduct);
  }

  function addToCart(event) {
   const seletedTitle = event.detail; 
   cardItems = cardItems.concat({...products.find(prod => prod.title === seletedTitle)});
   console.log(cardItems);
  }
</script>

<section>
  <Card items={cardItems}/>
</section>
<hr>
<section>
  <div>
    <label for="title">Title</label>
    <input type="text" id="title" value={title} on:input={setTitle} />
  </div>
  <div>
    <label for="price">Price</label>
    <input type="number" id="price" bind:value={price} />
  </div>
  <div>
    <label for="description">Description</label>
    <textarea rows="3" id="description" bind:value={description} />
  </div>
  <Button on:click={createProduct}>Create Product</Button>
</section>

<section>
  {#if products.length === 0}
    <p>No products were added yet!</p>
  {:else}
    {#each products as product}
      <Product
        productTitle={product.title}
        productPrice={product.price}
        productDescription={product.description}
        on:addcart={addToCart}
      />
    {/each}
  {/if}
</section>

<style>
  section {
    width: 30rem;
    margin: auto;
  }
  label,
  input,
  textarea {
    width: 100%;
  }
</style>
