<script lang="ts">
  import { onMount } from "svelte";
  import Header from "./Header.svelte";
  import About from "./About.svelte";
  import Experience from "./Experience.svelte";
  import CustomFidgets from "./projects/CustomFidgets.svelte";
  import ProstheticHand from "./projects/ProstheticHand.svelte";
  import MillenniumFalcon from "./projects/MillenniumFalcon.svelte";
  import Hammer from "./projects/Hammer.svelte";
  import CarpetSweeper from "./projects/CarpetSweeper.svelte";

  let activeSection = "";
  let diamondGifElement: HTMLImageElement | null = null;

  function setActiveSection(sectionId: string) {
    activeSection = sectionId;
  }

  onMount(() => {
    function updateActiveSection() {
      const viewportTop = window.scrollY + 150; // Offset for header
      const sections = document.querySelectorAll("[data-project-section]");
      const sectionsArray = Array.from(sections);

      // Check if we're at the bottom of the page
      const isAtBottom =
        window.innerHeight + window.scrollY >=
        document.documentElement.scrollHeight - 100;

      if (isAtBottom && sectionsArray.length > 0) {
        // If at bottom, activate the last section
        const lastSection = sectionsArray[sectionsArray.length - 1];
        const lastSectionId = lastSection.getAttribute("data-project-section");
        if (lastSectionId) {
          activeSection = lastSectionId;
        }
        return;
      }

      // Find the section closest to the top of the viewport
      let closestSection = "";
      let closestDistance = Infinity;

      sectionsArray.forEach((section) => {
        const rect = section.getBoundingClientRect();
        const sectionTop = rect.top + window.scrollY;
        const sectionId = section.getAttribute("data-project-section");

        if (sectionId) {
          // Calculate distance from section top to viewport top
          const distance = Math.abs(sectionTop - viewportTop);

          // Only consider sections that are at or above the viewport top, or very close below
          if (sectionTop <= viewportTop + 200) {
            if (distance < closestDistance) {
              closestDistance = distance;
              closestSection = sectionId;
            }
          }
        }
      });

      if (closestSection) {
        activeSection = closestSection;
      }
    }

    window.addEventListener("scroll", updateActiveSection);
    updateActiveSection();

    diamondGifElement = document.getElementById(
      "diamond_gif",
    ) as HTMLImageElement | null;
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

<div class="min-h-screen bg-background">
  <Header {activeSection} {setActiveSection} />

  <main class="w-full pt-24 lg:pt-40">
    <div class="max-w-5xl mx-auto px-6 lg:px-8">
      <div class="space-y-24 lg:space-y-32 py-24 pb-24">
        <About />
        <Experience />
        <CustomFidgets />
        <ProstheticHand />
        <MillenniumFalcon />
        <Hammer />
        <CarpetSweeper />
      </div>
    </div>
  </main>
</div>
