<script>
    import { onMount } from "svelte"

    let blob

    onMount(() => {
        document.addEventListener("pointermove", handlePointerMove)
        return () => {
            document.removeEventListener("pointermove", handlePointerMove)
        }
    })

    function handlePointerMove(event) {
        const { clientX, clientY } = event
        blob.animate({ left: `${clientX}px`, top: `${clientY}px` }, { duration: 8000, fill: "forwards" })
    }
</script>

<div on:mousemove={handlePointerMove} bind:this={blob} class="mouse-effect" />
<div class="blur" />

<style>
    .mouse-effect {
        top: 50%;
        left: 50%;
        position: absolute;
        transform: translate(-50%, -50%);
        background-color: rgba(161, 121, 69, 0.5);
        border-radius: 50%;
        animation: blob 30s infinite;
        z-index: -1;
    }

    .blur {
        top: 0;
        left: 0;
        height: 100vh;
        width: 100vw;
        position: fixed;
        z-index: 1;
        backdrop-filter: blur(10rem);
    }

    @keyframes blob {
        0% {
            aspect-ratio: 1;
            height: 25rem;
            transform: translate(-50%, -50%) scale(1);
        }
        50% {
            aspect-ratio: 1.5;
            height: 15rem;
            transform: translate(-50%, -50%) scale(1.1) rotate(180deg);
        }
        100% {
            aspect-ratio: 1;
            height: 25rem;
            transform: translate(-50%, -50%) scale(1) rotate(180deg);
        }
    }

    @media screen and (max-width: 768px) {
        .mouse-effect {
            display: none;
        }
    }
</style>
