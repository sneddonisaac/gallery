<script>
    import Menu from "./Menu.svelte";

    const socials = [
    {
      name: "Instagram",
      href: "https://instagram.com",
      icon: "/src/assets/instagram.svg"
    },
    {
      name: "LinkedIn",
      href: "https://linkedin.com",
      icon: "/src/assets/linkedin.svg"
    },
    {
      name: "Twitter",
      href: "https://twitter.com",
      icon: "/src/assets/twitter.svg"
    }
  ];
</script>

<nav>
  <div class="grid">
    <div
      style="display: flex; justify-content: space-evenly; align-items: center; width: 50%;"
    >
      {#each socials as social}
        <a target="_blank" style="display: flex" href={social.href}>
          <img class="icon" alt={social.name} src={social.icon} />
        </a>
      {/each}
    </div>
    <a class="logo" href="/">Gallery</a>
    <Menu />
  </div>
</nav>

<style lang="scss">
  nav {
    position: fixed;
    top: 0;
    width: 100%;
    padding: 2rem 0;

    .grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      place-items: center;
    }

    .logo {
      font-size: x-large;
      font-weight: bold;
    }

    .icon {
      height: 25px;
      width: 25px;
      opacity: 50%;
      transition: opacity;
      transition-duration: 350ms;
      transition-timing-function: ease-in-out;

      &:hover {
        opacity: 100%;
      }
    }
  }
</style>
