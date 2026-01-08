<script lang="ts">
  import { onMount } from 'svelte';
  import Sidebar from './Sidebar.svelte';
  import { cn } from '$lib/utils';
  
  let activeSection = '';
  let diamondGifElement: HTMLImageElement | null = null;

  const projects = [
    {
      id: 'custom-fidgets',
      title: 'Custom Fidgets',
      paragraphs: [
        'Fidgets offer tactile stimulus to occupy restless energy that can disrupt concentration. Frustrated by noisy, distracting mainstream options, I design quiet, tactilely satisfying fidgets to subtly enhance focus.',
        'I originally designed "the perfect fidget" for myself, but when my peers asked to buy it from me, I knew I had to make something for them. Inspired by their feedback, I use CAD tools and 3D printing to refine my tactile and mechanical actions to create a compelling user experience.',
        'In fact, when placed in public settings, my creations rarely sit idle for long; people instinctively reach for them, effortlessly channeling distraction into calm productivity.'
      ],
      images: [
        { src: '/pics/fidgets.png', alt: 'Various fidget designs' }
      ],
      subProjects: [
        {
          title: 'Fidget Cube',
          listItems: [
            'Six different combinations of textures and dynamic tactile experiences.',
            'Magnetic slider, embedded ball bearings, gears, wheel, and joystick.',
            'All in a 1¼ inch cube.'
          ],
          images: [
            { src: '/pics/cube_exploded_view.png', alt: 'Fidget Cube Exploded View', class: 'cube-exploded' }
          ]
        },
        {
          title: 'Diamond Spinner',
          paragraphs: [
            '2 identical magnetic sides that rotate about a pin. Satisfying in its simplicity. Comes in variety of colors.'
          ],
          images: [
            { src: '/pics/diamond_spinner.png', alt: 'Diamond Spinner', belowText: true },
            { src: '/pics/diamond_spinner.gif', alt: 'Diamond Spinner in action', gif: true }
          ]
        }
      ]
    },
    {
      id: 'prosthetic-hand',
      title: 'Prosthetic Card-holding Hand',
      paragraphs: [
        'As a class project, I prototyped a card-holding prosthetic for a below-elbow amputee. Features include:'
      ],
      listItems: [
        { text: 'Sweat wicking adjustable attachment points' },
        { text: 'Scrabble-like holder with a capacity of 25 playing cards (6 if sides do not overlap)' },
        { text: 'Customizable front design' },
        { text: 'The card-holding portion can be detached easily to stand on a flat surface' }
      ],
      images: [
        { src: '/pics/card_older.png', alt: 'Prosthetic Card-holding Hand' }
      ]
    },
    {
      id: 'millennium-falcon',
      title: 'Millennium Falcon',
      paragraphs: [
        'I taught myself how to use Blender and Fusion 360 by modeling the Millennium Falcon from Star Wars from reference photos. Using my university\'s 3D printer to print the ship inspired me to get my own printer.',
        'I am currently modeling the ship in Solidworks.'
      ],
      cadImages: [
        { src: '/pics/mf_in_blender.png', alt: 'Millennium Falcon in Blender' },
        { src: '/pics/mf_in_fusion.png', alt: 'Millennium Falcon in Fusion 360' }
      ],
      images: [
        { src: '/pics/mf_printed.png', alt: '3D Printed Millennium Falcon' }
      ]
    },
    {
      id: 'hammer',
      title: '0.005" Tolerance Hammer',
      paragraphs: [
        'During a manufacturing class at Case Western, I learned the fundamentals of metal machining enabling me to make a hammer with 0.005" tolerances.',
        'The tools I used to make this steel hammer include:'
      ],
      listItems: [
        { text: 'Bandsaw' },
        { text: 'Lathe' },
        { text: 'Mill', subItems: ['Reamer'] },
        { text: 'Drill press', subItems: ['Counterbore', 'Countersink'] },
        { text: 'Benchtop Grinder and Polishing Wheel' },
        { text: 'Threaded Tap Wrench' },
        { text: 'CNC mill' }
      ],
      images: [
        { src: '/pics/hammer.png', alt: 'Precision Hammer' }
      ],
      isHammer: true
    },
    {
      id: 'carpet-sweeper',
      title: 'Carpet Sweeper',
      paragraphs: [
        'As part of a group project, I designed a broom with a belt-driven brush, to work as an unpowered vacuum cleaner. The design complied with Case\'s engineering documentation standards. It was manufacturable with the tools available in a standard machine shop, and had a cost of materials in line with the purpose it served.'
      ],
      images: [
        { src: '/pics/sweeper.png', alt: 'Carpet Sweeper Design' }
      ]
    }
  ];

  function updateActiveSection() {
    const scrollPosition = window.scrollY;
    const sections = document.querySelectorAll('[data-project-section]');
    
    sections.forEach((section) => {
      const sectionTop = section.getBoundingClientRect().top + scrollPosition - 100;
      const sectionBottom = sectionTop + section.getBoundingClientRect().height;
      const sectionId = section.getAttribute('data-project-section');
      
      if (scrollPosition >= sectionTop && scrollPosition < sectionBottom && sectionId) {
        activeSection = sectionId;
      }
    });
  }

  onMount(() => {
    window.addEventListener('scroll', updateActiveSection);
    updateActiveSection();

    diamondGifElement = document.getElementById('diamond_gif') as HTMLImageElement | null;
    if (diamondGifElement) {
      const interval = setInterval(() => {
        if (diamondGifElement) {
          diamondGifElement.src = diamondGifElement.src;
        }
      }, 3400);
      
      return () => clearInterval(interval);
    }
  });
</script>

<div class="flex min-h-screen flex-col lg:flex-row bg-background">
  <Sidebar {activeSection} />
  
  <main class="flex-1 lg:ml-64">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-12 py-12 lg:py-20">
      <header class="mb-16 lg:mb-24">
        <h1 class="text-4xl sm:text-5xl lg:text-6xl font-light tracking-tight mb-3">Engineering Portfolio</h1>
        <div class="h-px w-16 bg-gradient-to-r from-primary/60 to-transparent"></div>
      </header>

      <div class="space-y-24 lg:space-y-32">
        {#each projects as project}
          <section 
            id={project.id} 
            data-project-section={project.id}
            class="scroll-mt-24"
          >
            <div class="space-y-8">
              <div>
                <h2 class="text-2xl sm:text-3xl lg:text-4xl font-light tracking-tight mb-2">
                  {project.title}
                </h2>
                <div class="h-px w-12 bg-gradient-to-r from-primary/40 to-transparent"></div>
              </div>

              <div class="grid grid-cols-1 lg:grid-cols-[1.2fr_1fr] gap-8 lg:gap-16 items-start">
                <div class="space-y-6 text-muted-foreground/90 leading-relaxed order-2 lg:order-1">
                  {#if project.paragraphs}
                    {#each project.paragraphs as paragraph}
                      <p class="text-base sm:text-lg">{paragraph}</p>
                    {/each}
                  {/if}

                  {#if project.listItems}
                    <ul class="space-y-2.5 text-base sm:text-lg">
                      {#each project.listItems as item}
                        <li class="flex gap-3">
                          <span class="text-primary/60 mt-1.5">•</span>
                          <span>
                            {#if typeof item === 'string'}
                              {item}
                            {:else}
                              {item.text}
                              {#if item.subItems}
                                <ul class="ml-4 mt-1.5 space-y-1.5 text-sm text-muted-foreground/70">
                                  {#each item.subItems as subItem}
                                    <li class="flex gap-2">
                                      <span class="text-primary/40">-</span>
                                      <span>{subItem}</span>
                                    </li>
                                  {/each}
                                </ul>
                              {/if}
                            {/if}
                          </span>
                        </li>
                      {/each}
                    </ul>
                  {/if}

                  {#if project.cadImages}
                    <div class="grid grid-cols-2 gap-4 mt-8">
                      {#each project.cadImages as cadImage}
                        <div class="overflow-hidden rounded-sm">
                          <img src={cadImage.src} alt={cadImage.alt} class="w-full h-auto object-cover" />
                        </div>
                      {/each}
                    </div>
                  {/if}
                </div>

                <div class="space-y-6 order-1 lg:order-2">
                  {#each project.images as image}
                    <div class="overflow-hidden rounded-sm bg-card/50">
                      <img 
                        src={image.src} 
                        alt={image.alt} 
                        class={cn(
                          "w-full h-auto object-cover transition-transform duration-700 hover:scale-[1.02]",
                          project.isHammer && "lg:scale-110 lg:translate-x-4"
                        )}
                      />
                    </div>
                  {/each}
                </div>
              </div>

              {#if project.subProjects}
                <div class="space-y-12 mt-16 pt-12 border-t border-border/50">
                  {#each project.subProjects as subProject}
                    <div class="space-y-6">
                      <h3 class="text-xl sm:text-2xl font-light text-foreground">{subProject.title}</h3>
                      
                      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 lg:gap-12 items-start">
                        <div class="space-y-4 text-muted-foreground/90 text-base sm:text-lg leading-relaxed">
                          {#if subProject.paragraphs}
                            {#each subProject.paragraphs as paragraph}
                              <p>{paragraph}</p>
                            {/each}
                          {/if}
                          {#if subProject.listItems}
                            <ul class="space-y-2.5">
                              {#each subProject.listItems as item}
                                <li class="flex gap-3">
                                  <span class="text-primary/60 mt-1.5">•</span>
                                  <span>{item}</span>
                                </li>
                              {/each}
                            </ul>
                          {/if}
                          {#each subProject.images as image}
                            {#if image.belowText}
                              <div class="mt-6 overflow-hidden rounded-sm">
                                <img src={image.src} alt={image.alt} class="w-full h-auto" />
                              </div>
                            {/if}
                          {/each}
                        </div>
                        
                        <div class="flex items-center justify-center lg:justify-start">
                          {#each subProject.images as image}
                            {#if !image.belowText}
                              <div class={cn(
                                "overflow-hidden rounded-sm",
                                image.class === 'cube-exploded' ? "max-w-[280px] lg:max-w-[320px] mx-auto" : "max-w-full"
                              )}>
                                <img 
                                  src={image.src} 
                                  alt={image.alt} 
                                  class={cn(
                                    "w-full h-auto",
                                    image.class
                                  )}
                                  id={image.gif ? 'diamond_gif' : ''}
                                />
                              </div>
                            {/if}
                          {/each}
                        </div>
                      </div>
                    </div>
                  {/each}
                </div>
              {/if}
            </div>
          </section>
        {/each}
      </div>
    </div>
  </main>
</div>

<style>
  :global(.cube-exploded) {
    transform: rotate(90deg);
    transition: transform 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  }

  :global(.cube-exploded:hover) {
    transform: rotate(90deg) scale(1.03);
  }
</style>
