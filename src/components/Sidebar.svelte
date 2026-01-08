<script lang="ts">
  let { activeSection = '' }: { activeSection?: string } = $props();
  
  const navItems = [
    { id: 'custom-fidgets', label: 'Custom Fidgets' },
    { id: 'prosthetic-hand', label: 'Prosthetic Card-holding Hand' },
    { id: 'millennium-falcon', label: 'Millennium Falcon' },
    { id: 'hammer', label: 'Precision Hammer' },
    { id: 'carpet-sweeper', label: 'Carpet Sweeper' }
  ];

  function handleClick(e: MouseEvent, id: string) {
    e.preventDefault();
    const target = document.getElementById(id);
    if (target) {
      target.scrollIntoView({ behavior: 'smooth', block: 'start' });
    }
  }
</script>

<aside class="lg:fixed relative lg:w-52 w-full lg:h-screen h-auto bg-sidebar/50 border-r border-border/30 overflow-y-auto z-50">
  <div class="p-6 lg:p-8 lg:pt-10 space-y-8">
    <div class="space-y-3 pb-6 border-b border-border/30">
      <h2 class="text-lg font-semibold text-foreground">Jacob Niv</h2>
      <p class="text-xs text-muted-foreground/80 uppercase tracking-wide">Biomedical Engineer</p>
      <div class="space-y-1.5 text-xs">
        <a 
          href="mailto:jacobniv2187@gmail.com" 
          class="block text-primary/80 hover:text-primary transition-colors"
        >
          jacobniv2187@gmail.com
        </a>
        <a 
          href="https://jacobniv.xyz" 
          target="_blank"
          rel="noopener noreferrer"
          class="block text-primary/80 hover:text-primary transition-colors"
        >
          jacobniv.xyz
        </a>
      </div>
      <div class="pt-2 space-y-3 text-xs text-muted-foreground/70">
        <div class="space-y-1.5">
          <p class="font-medium text-muted-foreground/90">Education</p>
          <p>Case Western Reserve University</p>
          <p>B.S. Biomedical Engineering</p>
          <p>Biomechanics • May 2027</p>
          <p class="pt-1">GPA: 3.32</p>
        </div>
        <div class="space-y-1.5 pt-2 border-t border-border/30">
          <p class="font-medium text-muted-foreground/90">Experience</p>
          <div class="space-y-2">
            <div>
              <p class="font-medium text-muted-foreground/90">President & External Affairs</p>
              <p>Network for Environmental Medical Outreach</p>
              <p class="text-muted-foreground/60">Jan 2024 - Present</p>
            </div>
            <div>
              <p class="font-medium text-muted-foreground/90">Research Lab Assistant</p>
              <p>Jay Lab - UMD</p>
              <p class="text-muted-foreground/60">Jun 2022 - Aug 2022</p>
            </div>
          </div>
        </div>
      </div>
    </div>
    
    <nav class="space-y-0.5">
      {#each navItems as item}
        <a
          href="#{item.id}"
          class="block px-3 py-2 text-xs font-medium transition-all duration-200 {activeSection === item.id 
            ? 'text-foreground border-l-2 border-primary pl-4' 
            : 'text-muted-foreground/70 hover:text-foreground hover:pl-4 pl-3'}"
          onclick={(e) => handleClick(e, item.id)}
        >
          {item.label}
        </a>
      {/each}
    </nav>
  </div>
</aside>
