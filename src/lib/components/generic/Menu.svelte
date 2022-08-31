<script>
    let open = false;

    function handleOpen() {
        open = !open;
    }
</script>

<div>
    <button on:click|preventDefault={handleOpen}> Menu </button>
</div>

<div data-state={open ? 'open' : 'closed'} id="menu">
    <button class="close-button" on:click|preventDefault={handleOpen}>
        X
    </button>
    <span>Home</span>
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
