<script>
  let open = false;

  function handleClick() {
    open = !open;
  }

  const navigation = [
    {
      name: "Clusters",
      href: "#clusters"
    }
  ];
</script>

<div>
  <button on:click|preventDefault={handleClick}> Menu</button>
</div>

<div data-state={open ? 'open' : 'closed'} id="menu">
  <button class="close-button" on:click|preventDefault={handleClick}>
    X
  </button>
  <div>
    {#each navigation as item}
      <a href={item.href} on:click={handleClick}>{item.name}</a>
    {/each}

  </div>
</div>

<style lang="scss">
  @keyframes fadeIn {
    from {
      opacity: 0;
    }
    to {
      opacity: 1;
    }
  }

  @keyframes fadeOut {
    from {
      opacity: 1;
    }
    to {
      opacity: 0;
    }
  }

  #menu {
    position: absolute;
    inset: 0;
    z-index: 100;
    background: #242424;
    height: 100vh;
    width: 100vw;

    &[data-state='open'] {
      display: block;
      animation: fadeIn 350ms ease-out;
    }

    &[data-state='closed'] {
      animation: fadeOut 350ms ease-out;
      display: none;
    }

    .close-button {
      position: absolute;
      top: 2rem;
      right: 2rem;
    }
  }
</style>
