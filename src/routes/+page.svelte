<style lang="scss">  
$color: purple;
  .container {
    color: $color;
    
    &:hover {
      color: adjust($color, 10%);
    }
  }
</style>

<section class="container">
  <h1 class="dancing-script-deco">Welcome to SvelteKit</h1>
  <p>Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the documentation</p>
</section>
