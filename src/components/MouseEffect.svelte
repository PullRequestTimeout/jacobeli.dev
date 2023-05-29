<script>
    // Create variables to store the mouse coordinates
    let mouseX = 0
    let mouseY = 0

    // Function to update the mouse coordinates
    const updateMousePosition = (event) => {
        mouseX = event.clientX
        mouseY = event.clientY
    }

    // Event listener to track mouse movement
    document.addEventListener("mousemove", updateMousePosition)
</script>

<div on:mousemove={updateMousePosition} style="top: {mouseY}px; left: {mouseX}px;" class="mouse-effect" />

<!-- <div on:mousemove={updateMousePosition} class="mouse-effect" /> -->

<style>
    .mouse-effect {
        top: 0;
        left: 0;
        position: absolute;
        height: 35rem;
        aspect-ratio: 1;
        transform: translate(-50%, -50%);
        background-color: #a17945;
        border-radius: 50%;
        filter: blur(10rem);
    }
</style>
