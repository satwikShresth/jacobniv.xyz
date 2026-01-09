<script lang="ts">
  let { id = 'prosthetic-hand' }: { id?: string } = $props();
  
  const paragraph = 'As team lead for a class project, I led a group to design and build a prosthetic to restore a below-elbow amputee\'s ability to hold and hide playing cards. Features include:';
  
  const listItems = [
    'Sweat wicking adjustable attachment points',
    'Scrabble-like holder with a capacity of 25 playing cards (6 if sides do not overlap)',
    'Customizable front design',
    'The card-holding portion can be detached easily to stand on a flat surface'
  ];
</script>

<section {id} data-project-section={id} class="scroll-mt-32 mb-20 pb-20 border-b border-border/20">
  <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 lg:gap-12">
    <div class="lg:col-span-4">
      <div class="text-xs uppercase tracking-widest text-muted-foreground mb-2">Project 02</div>
      <h2 class="text-3xl lg:text-4xl font-semibold mb-6 text-foreground" style="font-family: 'Playfair Display', serif;">
        Prosthetic Card&#8209;holding Hand
      </h2>
    </div>
    
    <div class="lg:col-span-8 space-y-6">
      <img src="/pics/card_older.png" alt="Prosthetic Card-holding Hand" class="w-full rounded" />
      <div class="space-y-4 text-foreground leading-relaxed text-lg">
        <p>{paragraph}</p>
        <ul class="space-y-2.5 list-disc pl-6">
          {#each listItems as item}
            <li>{item}</li>
          {/each}
        </ul>
      </div>
    </div>
  </div>
</section>
