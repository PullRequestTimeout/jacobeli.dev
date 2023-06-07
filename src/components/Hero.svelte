<section>
    <div class="title">
        <h3 class="baloo">Jacob Druery</h3>
        <h2 class="mulish">Creative Developer</h2>
    </div>
    <p class="subtitle baloo">Crafting bespoke web experiences</p>
</section>

<style>
    section {
        margin-top: 30vh;
        display: grid;
        gap: 2rem;
        grid-template-columns: fit-content(8ch);
    }

    .title {
        display: flex;
        flex-direction: column;
        gap: 0.25rem;
    }
    h2,
    h3 {
        text-transform: uppercase;
        font-weight: 300;
    }

    h2 {
        font-size: 3rem;
        /* transform: translateX(-4px); */
        animation: slide-in 0.5s ease-in-out;
    }

    /* @keyframes slide-in {
        from {
            transform: translateY(100%);
        }
        to {
            transform: translateY(0%);
        }
    } */

    @media screen and (min-width: 360px) {
        h2 {
            font-size: 3.7rem;
        }
    }

    @media screen and (min-width: 640px) {
        h2 {
            font-size: 4.5rem;
        }
    }

    @media screen and (min-width: 768px) {
        section {
            grid-template-columns: fit-content(8ch) auto;
            margin-top: 40vh;
            gap: 1rem;
        }

        h2 {
            font-size: 5rem;
        }

        .subtitle {
            align-self: end;
        }
    }

    @media screen and (min-width: 1024px) {
        section {
            margin-top: 50vh;
        }

        h2 {
            font-size: 7rem;
        }
    }

    @media screen and (min-width: 1280px) {
        section {
            margin-top: 40vh;
        }

        h2 {
            font-size: 9rem;
        }
    }

    @media screen and (min-width: 1536px) {
        section {
            margin-top: 35vh;
        }

        h2 {
            font-size: 11rem;
        }
    }

    /* 320, 640, 768, 1024, 1280, 1536, 1920 */
</style>
