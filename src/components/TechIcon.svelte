<script>
    let theme
    let lightSVG
    let darkSVG
    let illuminated
</script>

{#if theme == "dark"}
    <div class="svg-container">
        {lightSVG}
        <div>{illuminated}</div>
    </div>
{:else if theme == "light"}
    <div class="svg-container">
        {darkSVG}
        <div class="illuminated">{illuminated}</div>
    </div>
{/if}

<style>
</style>
