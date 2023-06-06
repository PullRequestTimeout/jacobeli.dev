<script>
    export let innerText
    export let type
    export let link = ""

    let rotate

    if (type == "download") {
        rotate = "30"
    } else if (type == "link") {
        rotate = "-30"
    }

    // Place resume PDF in public folder
    function downloadPDF() {
        const url = "/Jacob-Druery-Resume.pdf"
        fetch(url)
            .then((response) => response.blob())
            .then((blob) => {
                const link = document.createElement("a")
                link.href = URL.createObjectURL(blob)
                link.download = "Jacob-Druery-Resume.pdf"
                link.click()
                URL.revokeObjectURL(link.href)
            })
    }

    function followLink() {
        window.open(link, "_blank")
    }
</script>

{#if type == "download"}
    <button on:click={downloadPDF} class="button" style="--rotate: {`${rotate}deg`}"><span>{innerText}</span></button>
{:else if type == "link" && link != ""}
    <button on:click={followLink} class="button" style="--rotate: {`${rotate}deg`}"><span>{innerText}</span></button>
{/if}

<style>
    .button {
        position: relative;
        z-index: 300;
        padding: 1rem 4rem 1rem 1rem;
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
