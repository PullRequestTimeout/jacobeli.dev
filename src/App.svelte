<script>
    // Imports
    import MouseEffect from "./components/MouseEffect.svelte"
    import Overlay from "./components/Overlay.svelte"
    import Navbar from "./components/Navbar.svelte"
    import Hero from "./components/Hero.svelte"
    import Blurb from "./components/Blurb.svelte"
    import About from "./components/About.svelte"
    import Projects from "./components/Projects.svelte"
    import Footer from "./components/Footer.svelte"
    import Tech from "./components/Tech.svelte"
</script>

<Navbar />
<main>
    <Hero />
    <Blurb />
    <Projects />
    <About />
    <Tech />
</main>
<Footer />

<Overlay />
<MouseEffect />

<style>
    @import url("https://fonts.googleapis.com/css2?family=Baloo+2&family=Mulish:wght@200;400&display=swap");

    main {
        padding: 1rem;
    }

    @media screen and (min-width: 768px) {
        main {
            padding: 2rem;
        }
    }

    /* Breakpoints 320, 640, 768, 1024, 1280, 1536, 1920 */
</style>
