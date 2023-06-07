<script>
    import FancyButton from "./FancyButton.svelte"
</script>

<section>
    <div />
    <div class="blurb">
        <p class="baloo">
            My goal is to help your business thrive by creating effective, practical solutions that align with your company's objectives. I'm
            passionate about crafting captivating, beautiful experiences for the web. If you're looking to add a little polish to your corner of the
            internet, let's have a chat!
        </p>
        <FancyButton orientation="up" innerText="Get In Contact" url="#contact" />
    </div>
</section>

<style>
    section {
        margin-top: 2rem;
        display: grid;
        grid-template-columns: 1rem auto;
        grid-gap: 2rem;
    }

    .blurb {
        display: flex;
        flex-direction: column;
        gap: 1rem;
    }

    .blurb p {
        font-size: 1rem;
        line-height: 1.3;
    }

    @media screen and (min-width: 640px) {
        section {
            margin-top: 4rem;
            grid-template-columns: 2rem auto;
        }
    }

    .blurb {
        gap: 2rem;
    }

    .blurb p {
        font-size: 1.2rem;
    }

    @media screen and (min-width: 768px) {
        section {
            grid-template-columns: 15% auto;
        }

        .blurb p {
            font-size: 1.4rem;
        }
    }

    @media screen and (min-width: 1024px) {
        .blurb p {
            font-size: 1.6rem;
        }
    }

    @media screen and (min-width: 1280px) {
        section {
            grid-template-columns: 30% auto;
        }
    }

    @media screen and (min-width: 1536px) {
        section {
            margin-top: 6rem;
        }

        .blurb {
            gap: 3rem;
        }
    }

    /* Breakpoints 320, 640, 768, 1024, 1280, 1536, 1920 */
</style>
