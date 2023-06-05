<script>
    // Imports
    import MouseEffect from "./components/MouseEffect.svelte"
    import Overlay from "./components/Overlay.svelte"
    import Navbar from "./components/Navbar.svelte"
    import Hero from "./components/Hero.svelte"
    import ProjectCard from "./components/ProjectCard.svelte"
    import DownloadButton from "./components/DownloadButton.svelte"
    import { projects } from "./projects"
</script>

<main>
    <Navbar />
    <Hero />
    <!-- <p class="blurb"></p> -->
    <!-- <section class="works">
        <h2>Works</h2>
        {#each projects as project}
            <hr />
            <ProjectCard
                title={project.title}
                subtitle={project.subtitle}
                date={project.date}
                description={project.description}
                video={project.video}
                image={project.image}
                link={project.link}
            />
        {/each}
        <hr />
    </section> -->
    <!-- <section class="about">
        <h2></h2>
        <p></p>
        <DownloadButton />
    </section> -->
    <!-- <section class="technologies">

    </section> -->
    <!-- <footer class="contact">
        <h2></h2>
        <p></p>
        <div class="socials">
            <SocialLink />
            <SocialLink />
            <SocialLink />
            <SocialLink />
        </div>
    </footer> -->

    <Overlay />
    <MouseEffect />
</main>

<style>
    @import url("https://fonts.googleapis.com/css2?family=Baloo+2&family=Mulish:wght@200;400&display=swap");

    main {
        padding: 1rem;
    }
    /* Follow this up with all dimensions */
    @media screen and (min-width: 768px) {
        main {
            padding: 2rem;
        }
    }

    /* Breakpoints 320, 640, 768, 1024, 1280, 1536, 1920 */
</style>
