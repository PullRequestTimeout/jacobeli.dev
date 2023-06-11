<script>
    import { onMount } from "svelte"
    import ProjectModal from "./ProjectModal.svelte"

    // Props
    export let title
    export let subtitle
    export let date
    export let description
    export let image
    export let video
    export let link

    let checked = false

    const handleClose = () => {
        checked = false
    }

    let videoOffset
    let titleOffset
    let videoElement

    onMount(() => {
        videoElement.addEventListener("mouseenter", () => {
            // Delays playing video until CSS animation is finished
            setTimeout(() => videoElement.play(), 500)
        })

        videoElement.addEventListener("mouseout", () => {
            videoElement.pause()
            // This delays returning the video back to one until CSS animation is finished
            setTimeout(() => (videoElement.currentTime = 0), 500)
        })
    })
</script>

<article class="project-card" style="--title-offset: {`${titleOffset}px`}; --video-offset: {`${videoOffset}px`}">
    <input type="checkbox" id={title + "checkbox"} bind:checked />
    <label for={title + "checkbox"}>
        <div class="project-card__text">
            <div bind:offsetHeight={titleOffset} class="project-card__title">
                <h2 class="mulish">{title}</h2>
                <h3 class="mulish">{subtitle}</h3>
                <p class="mulish">// {date}</p>
            </div>
            <p class="project-card__description baloo">{description}</p>
        </div>
    </label>

    <a href={link} class="project-card__media" target="_blank">
        <div>
            <video bind:offsetHeight={videoOffset} bind:this={videoElement} loop muted>
                <source src={video} type="video/mp4" />
            </video>
            <img class="project-card__img" src={image} alt="Screenshot of a project" />
        </div>
    </a>
</article>
<div class="modal">
    <ProjectModal {title} {subtitle} {date} {description} {image} {link} on:close={handleClose} open={checked} />
</div>

<style>
    label {
        cursor: pointer;
    }

    input[type="checkbox"] {
        display: none;
    }

    .project-card {
        width: 100%;
        display: grid;
        grid-template-columns: 1fr;
        overflow: hidden;
        height: var(--title-offset);
        transition: 0.5s;
        margin: 1rem 0;
    }

    .project-card__description {
        opacity: 0;
        transition: 0.3s;
    }

    /* .project-card:hover {
        height: var(--video-offset);
    } */

    .project-card:hover .project-card__description {
        opacity: 1;
        transition-delay: 0.4s;
    }

    .project-card__text {
        line-height: 1.6;
    }

    .project-card__title {
        padding-bottom: 1rem;
    }

    .project-card__title h2 {
        font-size: 2rem;
    }

    .project-card__title h2,
    .project-card__title h3 {
        text-transform: uppercase;
    }

    .project-card__media {
        position: relative;
        display: none;
    }

    .project-card__media video {
        object-fit: cover;
        width: 100%;
        aspect-ratio: 16/9;
        opacity: 0;
        transition: 0.5s ease;
    }

    .project-card__media video:hover {
        opacity: 1;
        transition-delay: 0.4s;
    }

    .project-card__img {
        position: absolute;
        z-index: -1;
        top: 0;
        left: 0;
        width: 100%;
    }
</style>
