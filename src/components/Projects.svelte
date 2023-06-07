<script>
    import ProjectCard from "./ProjectCard.svelte"
    import Title from "./Title.svelte"
    import { projects } from "../projects"
</script>

<section>
    <Title innerText="Selected Works" id="work" />
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
</section>
