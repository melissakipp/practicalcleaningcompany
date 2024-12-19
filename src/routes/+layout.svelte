<svelte:head>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
</svelte:head>

<script>
  import "../styles/global.scss";
  import Header from "../components/Header.svelte";
	import Footer from "../components/Footer.svelte";
</script>

<Header />
<main class="container">
  <slot />
</main>
<Footer />

<style lang="scss">
  .container {
    display: grid;
    grid-template-rows: auto 1fr auto;
    min-height: 100vh;
  }

  main {
    padding: 2rem;
  }
</style>