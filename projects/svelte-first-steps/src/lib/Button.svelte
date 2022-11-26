
<button on:click>
  <slot></slot>
</button>
<style>


  button {
    font: inherit;
    padding: 0.15 rem 0.5rem;
    background: #d10057;
    border: 1px solid #d10057;
    color: white;
    cursor: poin;
  }
  
  button:hover,
  button:active {
    box-shadow: 1px 1px 6px rgba(0,0,0,0.2);
  }

</style>