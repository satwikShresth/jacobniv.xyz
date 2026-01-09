<script lang="ts">
  let { id = "experience" }: { id?: string } = $props();

  const experiences = [
    {
      title: "President & External Affairs",
      company: "Network for Environmental Medical Outreach",
      location: "Cleveland, OH",
      dates: "January 2024 - Present",
      responsibilities: [
        "Demonstrate the environment's importance in human health to CWRU and Cleveland",
        "Coordinate collaborations, guest speakers, and funding from external organizations and industry mentors",
        "Ensure operations reflect club constitution, drive membership, and cooperate with university guidelines",
      ],
    },
    {
      title: "Research Lab Assistant",
      company:
        "Jay Lab - Department of Bioengineering at University of Maryland",
      location: "College Park, MD",
      dates: "June 2022 - August 2022",
      responsibilities: [
        "Researched and used novel methods for mechanically isolating extracellular vesicles from gut bacteria for drug delivery which resulted in improved purification yield",
        "Performed biochemical assays, microscopy, and spectroscopy for identification and quantification of results",
      ],
      publication: "https://pubmed.ncbi.nlm.nih.gov/37555379/",
    },
  ];
</script>

<section
  {id}
  data-project-section={id}
  class="scroll-mt-32 mb-20 pb-20 border-b border-border/20"
>
  <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 lg:gap-12">
    <div class="lg:col-span-4">
      <div class="text-xs uppercase tracking-widest text-muted-foreground mb-2">
        Experience
      </div>
      <h2
        class="text-3xl lg:text-4xl font-semibold mb-6 text-foreground"
        style="font-family: 'Playfair Display', serif;"
      >
        Work & Leadership
      </h2>
    </div>

    <div class="lg:col-span-8 space-y-8">
      {#each experiences as experience}
        <div class="space-y-3">
          <div>
            <h3 class="text-xl font-semibold text-foreground mb-1">
              {experience.title}
            </h3>
            <p class="text-base font-medium text-muted-foreground/90">
              {experience.company}
            </p>
            <p class="text-sm text-muted-foreground/70">
              {experience.location} • {experience.dates}
            </p>
          </div>
          <ul
            class="space-y-2 text-foreground leading-relaxed text-lg list-disc pl-6"
          >
            {#each experience.responsibilities as responsibility}
              <li>{responsibility}</li>
            {/each}
            {#if experience.publication}
              <li>
                Publication: <a
                  href={experience.publication}
                  target="_blank"
                  rel="noopener noreferrer"
                  class="text-primary hover:underline"
                >
                  Improved purification yield
                </a>
              </li>
            {/if}
          </ul>
        </div>
      {/each}
    </div>
  </div>
</section>
