<script>
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

<button on:click={downloadPDF} class="download">Download Resume</button>

<style>
    .download {
        position: relative;
        padding: 1rem 4rem 1rem 1rem;
        font-size: 1.2rem;
        border-radius: 2rem;
        border: none;
        background-color: #000;
        transition: 0.2s ease;
    }

    .download:hover {
        cursor: pointer;
        background-color: #a17945;
        color: #fff;
    }

    .download:hover::before {
        transform: translateY(-50%) rotate(30deg);
        color: #fff;
    }

    .download::before {
        content: "→";
        font-size: 1.8rem;
        font-family: sans-serif;
        position: absolute;
        display: flex;
        justify-content: center;
        height: 2.5rem;
        aspect-ratio: 1;
        border-radius: 50%;
        background-color: #a17945;
        color: #000;
        right: 0.55rem;
        top: 50%;
        transform: translateY(-50%);
        transition: 0.2s ease;
    }

    @media (prefers-color-scheme: dark) {
        .download {
            background-color: #fff;
            color: #000;
        }

        .download::before {
            color: #fff;
        }
    }
</style>
