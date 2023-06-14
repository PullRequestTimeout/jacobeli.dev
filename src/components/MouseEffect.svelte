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
        blob.animate({ left: `${clientX}px`, top: `${clientY}px` }, { duration: 5000, fill: "forwards" })
    }
</script>

<div class="container">
    <div on:mousemove={handlePointerMove} bind:this={blob} class="mouse-effect" />
</div>
<div class="blur" />

<style>
    .container {
        width: 100%;
        height: 100vh;
        position: fixed;
        z-index: -99;
        top: 0;
        left: 0;
        overflow: hidden;
    }

    .mouse-effect {
        display: none;
        top: 50%;
        left: 50%;
        position: absolute;
        transform: translate(-50%, -50%);
        background-color: rgba(161, 121, 69, 0.5);
        border-radius: 50%;
        animation: blob 30s infinite;
        z-index: -100;
    }

    .blur {
        top: 0;
        left: 0;
        height: 100vh;
        width: 100vw;
        position: fixed;
        z-index: -50;
        backdrop-filter: blur(5rem);
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

    @media screen and (min-width: 1024px) {
        .mouse-effect {
            display: unset;
        }
    }
</style>
