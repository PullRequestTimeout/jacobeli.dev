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

    // Opens a new tab if the link is not an id
    function followLink() {
        if (url.charAt(0) == "#") {
            window.location.href = url
        } else {
            window.open(url, "_blank")
        }
    }
</script>

<button on:click={followLink} class="button baloo" style="--rotate: {`${rotate}deg`}"><span>{innerText}</span></button>

<style>
    .button {
        position: relative;
        min-width: 10rem;
        width: max-content;
        text-align: left;
        z-index: 300;
        padding: 0.8rem 4rem 0.8rem 1rem;
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
        background-color: var(--clr-gold);
        color: var(--clr-white);
    }

    .button:hover::before {
        transform: translateY(-50%) rotate(var(--rotate));
        color: var(--clr-white);
    }

    .button:hover::after {
        transform: translateY(-50%) scale(10);
    }

    .button::before {
        content: "→";
        font-size: 1.8rem;
        font-family: sans-serif;
        z-index: 303;
        display: flex;
        justify-content: center;
        background-color: transparent;
    }

    .button::after {
        content: "";
        background-color: var(--clr-gold);
        z-index: 302;
    }

    .button::after,
    .button::before {
        transition: 0.2s ease;
        position: absolute;
        transform: translateY(-50%);
        right: 0.55rem;
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
