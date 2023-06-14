<script>
    import { createEventDispatcher } from "svelte"
    import FancyLink from "./FancyLink.svelte"

    export let title
    export let subtitle
    export let date
    export let description
    export let image
    export let link

    export let open = false

    const dispatch = createEventDispatcher()

    function handleClose() {
        open = false
        dispatch("close")
    }
</script>

<div class="blur" class:open />
<article class:open>
    <button on:click={handleClose} />
    <img src={image} alt={"Mockup of" + title} />
    <div>
        <h2 class="mulish">{title}</h2>
        <h3 class="mulish">{subtitle}</h3>
        <p class="mulish">// {date}</p>
        <hr />
        <p class="baloo">{description}</p>
        <FancyLink url={link} innerText={"View Live"} orientation="up" invert />
    </div>
</article>

<style>
    article {
        position: fixed;
        color: var(--clr-black);
        z-index: 500;
        height: 100vh;
        bottom: 0;
        left: 0;
        background-color: var(--clr-white);
        transform: translateY(100%);
        transition: 0.5s ease-out;
        overflow-y: scroll;
    }

    .blur {
        pointer-events: none;
        position: fixed;
        z-index: 499;
        top: 0;
        left: 0;
        width: 100vw;
        height: 100vh;
        backdrop-filter: blur(0);
        transition: 0.5s ease-in-out;
    }

    hr {
        width: 100%;
        border: none;
        border-bottom: 1px solid var(--clr-black);
    }

    h2,
    h3,
    p {
        line-height: 1.3;
    }

    h2 {
        font-size: 2rem;
    }

    h2,
    h3 {
        text-transform: uppercase;
    }

    div {
        padding: 1rem;
        display: flex;
        flex-direction: column;
    }

    img {
        width: 100%;
    }

    p.baloo {
        margin: 1.5rem 0 2rem 0;
    }

    button {
        cursor: pointer;
        position: absolute;
        top: 0;
        right: 0;
        width: 2rem;
        aspect-ratio: 1;
        border: none;
        background-color: transparent;
        margin: 0.5rem;
    }

    button::before,
    button::after {
        content: "";
        position: absolute;
        top: 50%;
        left: 0;
        height: 2px;
        width: 2rem;
        background-color: #fff;
    }

    button::before {
        transform: rotate(45deg);
    }

    button::after {
        transform: rotate(-45deg);
    }

    article.open {
        transform: translateY(0%);
    }

    div.open {
        backdrop-filter: blur(1rem);
    }

    @media screen and (min-width: 768px) {
        div {
            padding: 2rem;
        }
    }

    @media screen and (min-width: 1024px) {
        article,
        .blur {
            display: none;
        }
    }
</style>
