<script lang="ts">
  let { id = 'custom-fidgets' }: { id?: string } = $props();
  
  const paragraphs = [
    'Fidgets offer tactile stimulus to occupy restless energy that can disrupt concentration. Frustrated by noisy, distracting mainstream options, I design quiet, tactilely satisfying fidgets to subtly enhance focus.',
    'I originally designed "the perfect fidget" for myself, but when my peers asked to buy it from me, I knew I had to make something for them. Inspired by their feedback, I use CAD tools and 3D printing to refine my tactile and mechanical actions to create a compelling user experience.',
    'In fact, when placed in public settings, my creations rarely sit idle for long; people instinctively reach for them, effortlessly channeling distraction into calm productivity.'
  ];
</script>

<section {id} data-project-section={id} class="scroll-mt-32 mb-20 pb-20 border-b border-border/20">
  <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 lg:gap-12">
    <div class="lg:col-span-4">
      <div class="text-xs uppercase tracking-widest text-muted-foreground mb-2">Project 01</div>
      <h2 class="text-3xl lg:text-4xl font-semibold mb-6 text-foreground" style="font-family: 'Playfair Display', serif;">
        Custom Fidgets
      </h2>
      <div class="pt-4">
        <img src="/pics/fidgets.png" alt="Various fidget designs" class="w-full rounded" />
      </div>
    </div>

    <div class="lg:col-span-8 space-y-8">
      <div class="space-y-4 text-foreground leading-relaxed text-lg">
        {#each paragraphs as paragraph}
          <p>{paragraph}</p>
        {/each}
      </div>

      <div class="space-y-12 pt-4">
        <div>
          <h3 class="text-2xl font-semibold mb-4 text-foreground" style="font-family: 'Playfair Display', serif;">
            Fidget Cube
          </h3>
          <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 items-start">
            <div class="space-y-3 text-foreground text-lg leading-relaxed">
              <ul class="space-y-2.5 list-disc pl-6">
                <li>Six different combinations of textures and dynamic tactile experiences.</li>
                <li>Magnetic slider, embedded ball bearings, gears, wheel, and joystick.</li>
                <li>All in a 1¼ inch cube.</li>
              </ul>
            </div>
            <div class="flex items-center justify-center">
              <div class="cube-image-wrapper">
                <img 
                  src="/pics/cube_exploded_view.png" 
                  alt="Fidget Cube Exploded View" 
                  class="cube-image"
                />
              </div>
            </div>
          </div>
        </div>

        <div>
          <h3 class="text-2xl font-semibold mb-4 text-foreground" style="font-family: 'Playfair Display', serif;">
            Diamond Spinner
          </h3>
          <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 items-start">
            <div class="space-y-4 text-foreground text-lg leading-relaxed">
              <p>2 identical magnetic sides that rotate about a pin. Satisfying in its simplicity. Comes in variety of colors.</p>
              <img src="/pics/diamond_spinner.png" alt="Diamond Spinner" class="w-full rounded mt-6" />
            </div>
            <div class="flex items-center justify-center">
              <img 
                src="/pics/diamond_spinner.gif" 
                alt="Diamond Spinner in action" 
                id="diamond_gif"
                class="w-full max-w-sm rounded"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<style>
  .cube-image-wrapper {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    min-height: 300px;
  }
  
  .cube-image {
    transform: rotate(90deg);
    width: auto;
    height: 100%;
    max-width: 450px;
    object-fit: contain;
  }
</style>
