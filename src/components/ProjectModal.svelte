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

<article class:open>
    <button on:click={handleClose} />
    <img src={image} alt={"Mockup of" + title} />
    <div>
        <h2 class="mulish">{title}</h2>
        <h3 class="mulish">{subtitle}</h3>
        <p class="mulish">// {date}</p>
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
    }

    h2 {
        font-size: 3rem;
    }

    h2,
    h3 {
        text-transform: uppercase;
    }

    div {
        padding: 1rem;
        display: flex;
        flex-direction: column;
        /* gap: 1rem; */
    }

    img {
        width: 100%;
        margin-top: 5vh;
    }

    p.baloo {
        margin: 1rem 0;
        line-height: 1.3;
    }

    button {
        position: absolute;
        top: 0;
        right: 0;
        width: 2rem;
        aspect-ratio: 1;
    }

    article.open {
        transform: translateY(0%);
    }
</style>
