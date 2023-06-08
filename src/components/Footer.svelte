<script>
    import SocialLink from "./SocialLink.svelte"
    import Title from "./Title.svelte"
</script>

<footer>
    <Title innerText="Contact" id="contact" invert />
    <p class="mulish">Got a project in mind?</p>
    <h3 class="mulish"><span>Let's</span> <span>Collaborate</span></h3>
    <div class="socials">
        <SocialLink innerText="Email" url="mailto:jacobedruery@gmail.com" svg="email" />
        <SocialLink innerText="Insta" url="https://www.instagram.com/caffeinatejake/" svg="insta" />
        <SocialLink innerText="Github" url="https://github.com/PullRequestTimeout" svg="github" />
        <SocialLink innerText="LinkedIn" url="https://www.linkedin.com/in/jacob-druery/" svg="linkedin" />
    </div>
</footer>

<style>
    footer {
        background-color: var(--clr-white);
        color: var(--clr-black);
        padding: 1rem;
        display: flex;
        flex-direction: column;
        gap: 2rem;
    }

    footer > * {
        text-transform: uppercase;
    }

    p {
        font-size: 1.2rem;
        text-align: center;
    }

    h3 {
        display: flex;
        justify-content: space-evenly;
        /* font-size: 9.622vw; */
        font-size: 8vw;
        text-align: center;
    }

    .socials {
        padding-left: 0.5rem;
        display: flex;
        justify-content: space-between;
        gap: 1rem;
    }

    @media screen and (min-width: 640px) {
        footer {
            padding: 2rem;
        }

        p {
            font-size: 1.5rem;
        }

        h3 {
            font-size: 9vw;
            text-align: justify;
        }

        .socials {
            justify-content: start;
        }
    }

    @media screen and (min-width: 768px) {
        h3 {
            font-size: 9.5vw;
        }
    }

    @media screen and (min-width: 1280px) {
        h3 {
            display: flex;
            justify-content: space-between;
        }
    }
</style>
