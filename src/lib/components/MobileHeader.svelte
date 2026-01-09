<script lang="ts">
  import { onMount } from "svelte";
  import ModeToggle from "./ModeToggle.svelte";

  let {
    activeSection = "",
    setActiveSection,
  }: { activeSection?: string; setActiveSection?: (id: string) => void } =
    $props();

  let projectsDropdownOpen = $state(false);
  let projectsDropdownRef = $state<HTMLDivElement | null>(null);

  const navItems = [
    { id: "about", label: "About" },
    { id: "experience", label: "Experience" },
  ];

  const projectItems = [
    { id: "custom-fidgets", label: "Product Design" },
    { id: "prosthetic-hand", label: "Prosthetic Device" },
    { id: "millennium-falcon", label: "CAD Modeling" },
    { id: "hammer", label: "Precision Machining" },
    { id: "carpet-sweeper", label: "Mechanical Design" },
  ];

  // Determine which navigation items to show
  let isInProjectsSection = $derived(
    projectItems.some((item) => activeSection === item.id),
  );

  function handleClick(e: MouseEvent, id: string) {
    e.preventDefault();
    if (setActiveSection) {
      setActiveSection(id);
    }
    const target = document.getElementById(id);
    if (target) {
      target.scrollIntoView({ behavior: "smooth", block: "start" });
    }
    projectsDropdownOpen = false;
  }

  onMount(() => {
    function handleClickOutside(e: MouseEvent) {
      if (
        projectsDropdownRef &&
        !projectsDropdownRef.contains(e.target as Node)
      ) {
        projectsDropdownOpen = false;
      }
    }

    document.addEventListener("click", handleClickOutside);

    return () => {
      document.removeEventListener("click", handleClickOutside);
    };
  });
</script>

<header
  class="fixed top-0 left-0 right-0 z-50 bg-background/95 backdrop-blur-xl border-b border-border/20 lg:hidden"
>
  <div class="max-w-5xl mx-auto px-4 py-3">
    <div class="flex items-center justify-between">
      <a
        href="/"
        class="text-foreground hover:opacity-80 text-xl font-semibold"
        style="font-family: 'Playfair Display', serif;"
      >
        Jacob Niv
      </a>
      <ModeToggle />
    </div>
    <nav class="flex items-center gap-4 text-sm mt-2 flex-wrap">
      {#if !isInProjectsSection}
        <!-- Default navigation: About, Experience, Projects dropdown -->
        {#each navItems as item}
          <a
            href="#{item.id}"
            class="relative transition-all duration-200 {activeSection ===
            item.id
              ? 'text-foreground font-semibold'
              : 'text-muted-foreground hover:text-foreground'}"
            onclick={(e) => handleClick(e, item.id)}
            data-s-event="Navigation: {item.label}"
            data-s-event-path="/#{item.id}"
          >
            {item.label}
            {#if activeSection === item.id}
              <span
                class="absolute -bottom-1.5 left-0 right-0 h-0.5 bg-primary rounded-full"
              ></span>
            {/if}
          </a>
        {/each}

        <!-- Projects Dropdown -->
        <div bind:this={projectsDropdownRef} class="relative" role="group">
          <button
            type="button"
            class="relative transition-all duration-200 text-muted-foreground hover:text-foreground"
            onclick={(e) => {
              e.stopPropagation();
              projectsDropdownOpen = !projectsDropdownOpen;
            }}
            onkeydown={(e) => {
              if (e.key === "Enter" || e.key === " ") {
                e.preventDefault();
                projectsDropdownOpen = !projectsDropdownOpen;
              }
            }}
            aria-expanded={projectsDropdownOpen}
            aria-haspopup="true"
          >
            Projects
          </button>

          {#if projectsDropdownOpen}
            <div
              class="absolute top-full left-0 mt-2 w-48 bg-background border border-border/50 rounded-lg shadow-lg py-2 z-50"
            >
              {#each projectItems as project}
                <a
                  href="#{project.id}"
                  class="block px-4 py-2 text-sm transition-colors duration-200 {activeSection ===
                  project.id
                    ? 'text-foreground font-medium bg-accent/50'
                    : 'text-muted-foreground hover:text-foreground hover:bg-accent/30'}"
                  onclick={(e) => handleClick(e, project.id)}
                  data-s-event="Project: {project.label}"
                  data-s-event-path="/#{project.id}"
                >
                  {project.label}
                </a>
              {/each}
            </div>
          {/if}
        </div>
      {:else}
        <!-- Projects navigation: Show all project names -->
        {#each projectItems as item}
          <a
            href="#{item.id}"
            class="relative transition-all duration-200 {activeSection ===
            item.id
              ? 'text-foreground font-semibold'
              : 'text-muted-foreground hover:text-foreground'}"
            onclick={(e) => handleClick(e, item.id)}
            data-s-event="Project: {item.label}"
            data-s-event-path="/#{item.id}"
          >
            {item.label}
            {#if activeSection === item.id}
              <span
                class="absolute -bottom-1.5 left-0 right-0 h-0.5 bg-primary rounded-full"
              ></span>
            {/if}
          </a>
        {/each}
      {/if}
    </nav>
  </div>
</header>
