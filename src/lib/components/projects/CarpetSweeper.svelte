<script lang="ts">
  let { id = 'carpet-sweeper' }: { id?: string } = $props();
  
  const paragraph = 'As part of a group project, I worked with a team to design a novel consumer product—a broom with a belt-driven brush that functions as an unpowered vacuum cleaner. The design complied with Case Western Reserve University\'s engineering documentation standards, was manufacturable with machine shop and factory tools, and had a cost of materials in line with the purpose it served.';
</script>

<section {id} data-project-section={id} class="scroll-mt-32 mb-20 pb-20 border-b border-border/20">
  <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 lg:gap-12">
    <div class="lg:col-span-4">
      <div class="text-xs uppercase tracking-widest text-muted-foreground mb-2">Project 05</div>
      <h2 class="text-3xl lg:text-4xl font-semibold mb-6 text-foreground" style="font-family: 'Playfair Display', serif;">
        Carpet Sweeper
      </h2>
    </div>

    <div class="lg:col-span-8 space-y-6">
      <img src="/pics/sweeper.png" alt="Carpet Sweeper Design" class="w-full rounded" />
      <div class="space-y-4 text-foreground leading-relaxed text-lg">
        <p>{paragraph}</p>
      </div>
    </div>
  </div>
</section>
