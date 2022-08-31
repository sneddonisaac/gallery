<script>
  import Navbar from "../generic/Navbar.svelte";
</script>

<main>
  <Navbar />
  <slot></slot>
</main>


<style>
    main {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
</style>