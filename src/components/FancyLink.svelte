<script>
    export let innerText
    export let orientation
    export let url = ""

    let rotate

    if (orientation == "down") {
        rotate = "30"
    } else if (orientation == "up") {
        rotate = "-30"
    }
</script>

{#if url.charAt(0) == "#"}
    <a href={url} class="button baloo" style="--rotate: {`${rotate}deg`}"><span>{innerText}</span></a>
{:else}
    <a href={url} class="button baloo" target="_blank" style="--rotate: {`${rotate}deg`}"><span>{innerText}</span></a>
{/if}

<style>
    .button {
        position: relative;
        display: flex;
        align-items: center;
        min-width: 8rem;
        /* min-height: 1.6rem; */
        width: max-content;
        text-align: left;
        z-index: 300;
        padding: 1.1rem 4rem 1rem 1rem;
        font-size: 1.2rem;
        border-radius: 2rem;
        border: none;
        background-color: var(--clr-black);
        transition: 0.2s ease;
        overflow: hidden;
    }

    .button span {
        position: relative;
        z-index: 304;
    }

    .button:hover {
        cursor: pointer;
    }

    .button:hover,
    .button:focus,
    .button:active {
        background-color: var(--clr-gold);
        color: var(--clr-white);
    }

    .button:hover::before,
    .button:focus::before,
    .button:active::before {
        transform: translateY(-45%) rotate(var(--rotate));
        color: var(--clr-white);
    }

    .button:hover::after,
    .button:focus::after,
    .button:active::after {
        transform: translateY(-50%) scale(10);
    }

    .button::before {
        content: "→";
        font-size: 1.8rem;
        font-family: sans-serif;
        z-index: 303;
        display: flex;
        justify-content: center;
        transform: translateY(-45%);
        background-color: transparent;
    }

    .button::after {
        content: "";
        background-color: var(--clr-gold);
        z-index: 302;
        transform: translateY(-50%);
    }

    .button::after,
    .button::before {
        transition: 0.2s ease;
        position: absolute;
        right: 0.5rem;
        height: 2.5rem;
        top: 50%;
        border-radius: 50%;
        aspect-ratio: 1;
    }

    @media (prefers-color-scheme: dark) {
        .button {
            background-color: var(--clr-white);
            color: var(--clr-black);
        }

        .button::before {
            color: var(--clr-white);
        }
    }
</style>
