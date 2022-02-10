<script>
  import Filter from "./Filter.svelte";
  import projects from "../data/projects.json";
  import ExternalLink from "../icons/ExternalLink.svelte";

  let filters = [
    ["Frontend", false],
    ["Backend", false],
    ["React Native", false],
  ];

  const toggleFilter = (i) => {
    filters[i][1] = !filters[i][1];
    filters = [...filters];
  };
</script>

<main>
  <!-- <section id="filter-section">
    <h5>Filters</h5>
    <div class="filters">
      {#each filters as filter, index}
        <Filter {filter} {index} {toggleFilter} />
      {/each}
    </div>
  </section> -->

  <section id="projects">
    {#each projects as project}
      <div class="project">
        <img src={project.image} alt={project.name} />
        <h2>{project.name}</h2>
        <p>{project.desc}</p>
        <div class="tags">
          {#each project.tags as tag}
            #{tag + " "}
          {/each}
        </div>
        {#if project.siteUrl}
          <a class="link-button" href={project.siteUrl}>
            View site&nbsp;<ExternalLink />
          </a>
        {/if}
        {#if project.githubUrl}
          <a class="link-button" href={project.githubUrl}>
            Github&nbsp;<ExternalLink />
          </a>
        {/if}
      </div>
    {/each}
  </section>
</main>

<style>
  h2 {
    font-size: var(--font-lg);
    margin: 12px 0 6px 0;
  }

  h5 {
    font-size: var(--font-sm);
    margin: 0 0 6px 0;
    text-transform: uppercase;
  }

  p {
    font-size: var(--font-sm);
    margin-bottom: 4px;
  }

  .tags {
    font-size: var(--font-xs);
    font-weight: bold;
  }

  .link-button {
    border: 1px solid black;
    border-radius: 50px;
    padding: 1px 14px;
    display: inline-flex;
    align-items: center;
    margin-right: 6px;
    margin-top: 10px;
    font-size: var(--font-sm);
    text-decoration: none;
    color: black;
  }
  .link-button:hover {
    background-color: lightgray;
  }

  #filter-section {
    background-color: #eeeeee;
    padding: 40px var(--padding);
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .filters {
    display: flex;
    flex-direction: row;
  }

  #projects {
    background-color: white;
    color: black;
    padding: var(--padding);
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-gap: 40px;
  }

  img {
    border-radius: 26px;
  }

  @media (max-width: 800px) {
    #projects {
      grid-template-columns: 100%;
      grid-gap: 40px;
    }
  }
</style>
