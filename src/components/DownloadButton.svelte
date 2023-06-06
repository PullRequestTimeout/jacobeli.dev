<script>
    export let text

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
</script>

<button on:click={downloadPDF} class="download"><span>{text}</span></button>

<style>
    .download {
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

    .download span {
        position: relative;
        z-index: 304;
    }

    .download:hover {
        cursor: pointer;
        background-color: var(--clr-gold);
        color: var(--clr-white);
    }

    .download:hover::before {
        transform: translateY(-50%) rotate(30deg);
        color: var(--clr-white);
    }

    .download:hover::after {
        transform: translateY(-50%) scale(10);
    }

    .download::before {
        content: "→";
        font-size: 1.8rem;
        font-family: sans-serif;
        z-index: 303;
        display: flex;
        justify-content: center;
        background-color: transparent;
    }

    .download::after {
        content: "";
        background-color: var(--clr-gold);
        z-index: 302;
    }

    .download::after,
    .download::before {
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
        .download {
            background-color: var(--clr-white);
            color: var(--clr-black);
        }

        .download::before {
            color: var(--clr-white);
        }
    }
</style>
