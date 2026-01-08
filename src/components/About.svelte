<script lang="ts">
  import Mail from "@lucide/svelte/icons/mail";
  import Linkedin from "@lucide/svelte/icons/linkedin";
  import FileText from "@lucide/svelte/icons/file-text";
  
  let { id = 'about' }: { id?: string } = $props();
  
  const summary = 'Biomedical engineer who combines a passion for tinkering, lab experience, and engineering principles to create intuitive, seamless designs for improving the quality of life in patients.';
</script>

<section {id} data-project-section={id} class="scroll-mt-32 mb-20 pb-20 border-b border-border/20">
  <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 lg:gap-12">
    <div class="lg:col-span-4">
      <div class="text-xs uppercase tracking-widest text-muted-foreground mb-2">About</div>
      <h2 class="text-3xl lg:text-4xl font-semibold mb-6 text-foreground" style="font-family: 'Playfair Display', serif;">
        About Me
      </h2>
    </div>
    
    <div class="lg:col-span-8 space-y-6">
      <div class="space-y-4 text-muted-foreground leading-relaxed text-base">
        <p class="text-lg">{summary}</p>
        <div class="flex items-center gap-4 flex-wrap">
          <a 
            href="/jn_resume.pdf" 
            target="_blank" 
            rel="noopener noreferrer"
            class="p-2 rounded-lg hover:bg-accent/50 transition-colors duration-200 border border-border/50 hover:border-border flex items-center justify-center gap-2 px-3"
            aria-label="Resume"
            data-s-event="Resume Download"
            data-s-event-path="/about"
          >
            <FileText class="h-4 w-4 text-muted-foreground" />
            <span class="text-sm text-muted-foreground">Resume</span>
          </a>
          <a 
            href="mailto:jacobniv2187@gmail.com"
            class="p-2 rounded-lg hover:bg-accent/50 transition-colors duration-200 border border-border/50 hover:border-border flex items-center justify-center gap-2 px-3"
            aria-label="Email"
            data-s-event="Email Click"
            data-s-event-path="/about"
          >
            <Mail class="h-4 w-4 text-muted-foreground" />
            <span class="text-sm text-muted-foreground">Email</span>
          </a>
          <a 
            href="https://www.linkedin.com/in/jacob-niv-56887033b/"
            target="_blank"
            rel="noopener noreferrer"
            class="p-2 rounded-lg hover:bg-accent/50 transition-colors duration-200 border border-border/50 hover:border-border flex items-center justify-center gap-2 px-3"
            aria-label="LinkedIn"
            data-s-event="LinkedIn Click"
            data-s-event-path="/about"
          >
            <Linkedin class="h-4 w-4 text-muted-foreground" />
            <span class="text-sm text-muted-foreground">LinkedIn</span>
          </a>
        </div>
      </div>
    </div>
  </div>
</section>
