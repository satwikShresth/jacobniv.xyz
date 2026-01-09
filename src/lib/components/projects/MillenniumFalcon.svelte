<script lang="ts">
  let { id = 'millennium-falcon' }: { id?: string } = $props();
  
  const paragraphs = [
    'I taught myself how to use Blender and Fusion 360 by modeling the Millennium Falcon from Star Wars from reference photos. Using my university\'s 3D printer to print the ship inspired me to get my own printer.',
    'I am currently modeling the ship in Solidworks.'
  ];
</script>

<section {id} data-project-section={id} class="scroll-mt-32 mb-20 pb-20 border-b border-border/20">
  <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 lg:gap-12">
    <div class="lg:col-span-4">
      <div class="text-xs uppercase tracking-widest text-muted-foreground mb-2">Project 03</div>
      <h2 class="text-3xl lg:text-4xl font-semibold mb-6 text-foreground" style="font-family: 'Playfair Display', serif;">
        Millennium Falcon
      </h2>
      <div class="grid grid-cols-2 gap-4 pt-4">
        <img src="/pics/mf_in_blender.png" alt="Millennium Falcon in Blender" class="w-full rounded" />
        <img src="/pics/mf_in_fusion.png" alt="Millennium Falcon in Fusion 360" class="w-full rounded" />
      </div>
    </div>

    <div class="lg:col-span-8 space-y-6">
      <div class="space-y-4 text-foreground leading-relaxed text-lg">
        {#each paragraphs as paragraph}
          <p>{paragraph}</p>
        {/each}
      </div>
      <img src="/pics/mf_printed.png" alt="3D Printed Millennium Falcon" class="w-full rounded" />
    </div>
  </div>
</section>
