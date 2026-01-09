<script lang="ts">
  let { id = 'hammer' }: { id?: string } = $props();
  
  const paragraphs = [
    'During a manufacturing class at Case Western, I learned the fundamentals of metal machining enabling me to make a hammer with 0.005" tolerances.',
    'The tools I used to make this steel hammer include:'
  ];
  
  const listItems = [
    { text: 'Bandsaw' },
    { text: 'Lathe' },
    { text: 'Mill', subItems: ['Reamer'] },
    { text: 'Drill press', subItems: ['Counterbore', 'Countersink'] },
    { text: 'Benchtop Grinder and Polishing Wheel' },
    { text: 'Threaded Tap Wrench' },
    { text: 'CNC mill' }
  ];
</script>

<section {id} data-project-section={id} class="scroll-mt-32 mb-20 pb-20 border-b border-border/20">
  <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 lg:gap-12">
    <div class="lg:col-span-4">
      <div class="text-xs uppercase tracking-widest text-muted-foreground mb-2">Project 04</div>
      <h2 class="text-3xl lg:text-4xl font-semibold mb-6 text-foreground" style="font-family: 'Playfair Display', serif;">
        0.005" Tolerance Hammer
      </h2>
    </div>
    
    <div class="lg:col-span-8 space-y-6">
      <img src="/pics/hammer.png" alt="Precision Hammer" class="w-full rounded" />
      <div class="space-y-4 text-foreground leading-relaxed text-lg">
        {#each paragraphs as paragraph}
          <p>{paragraph}</p>
        {/each}
        <ul class="space-y-2.5 list-disc pl-6">
          {#each listItems as item}
            <li>
              {item.text}
              {#if item.subItems}
                <ul class="ml-6 mt-1.5 space-y-1.5 list-disc pl-6 text-foreground">
                  {#each item.subItems as subItem}
                    <li>{subItem}</li>
                  {/each}
                </ul>
              {/if}
            </li>
          {/each}
        </ul>
      </div>
    </div>
  </div>
</section>
