<script>
    // Imports
    import MouseEffect from "./components/MouseEffect.svelte"
    import Overlay from "./components/Overlay.svelte"
    import Navbar from "./components/Navbar.svelte"
    import Hero from "./components/Hero.svelte"
    import Blurb from "./components/Blurb.svelte"
    import About from "./components/About.svelte"
    import Projects from "./components/Projects.svelte"
</script>

<main>
    <Navbar />
    <Hero />
    <Blurb />
    <Projects />
    <About />
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

    <!-- <Overlay /> -->
    <!-- <MouseEffect /> -->
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
