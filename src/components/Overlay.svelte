<script>
    import { onMount, onDestroy } from "svelte"

    let seed = Math.floor(Math.random() * 999) // Initial seed value

    const updateSeed = () => {
        seed = Math.floor(Math.random() * 999)
    }

    onMount(() => {
        const interval = setInterval(updateSeed, 20)

        onDestroy(() => {
            clearInterval(interval)
        })
    })
</script>

<div class="static-overlay" />
<svg>
    <defs>
        <filter id="static">
            <feTurbulence type="fractalNoise" baseFrequency="0.65" numOctaves="1" {seed} />
        </filter>
    </defs>
</svg>

<style>
    .static-overlay {
        position: fixed;
        z-index: 1000;
        top: 0;
        left: 0;
        width: 100vw;
        height: 100vh;
        opacity: 0.1;
        filter: url(#static);
    }
</style>
