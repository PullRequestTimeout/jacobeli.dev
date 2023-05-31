<script>
    import { onMount } from "svelte"

    let seed = Math.floor(Math.random() * 999) // Initial seed value

    onMount(() => {
        const updateSeed = () => {
            seed = Math.floor(Math.random() * 999)
        }
        setInterval(updateSeed, 20)
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
    svg {
        position: absolute;
        pointer-events: none;
    }

    .static-overlay {
        pointer-events: none;
        position: fixed;
        z-index: 1000;
        top: 0;
        left: 0;
        width: 100vw;
        height: 100vh;
        opacity: 0.2;
        filter: url(#static);
    }
</style>
