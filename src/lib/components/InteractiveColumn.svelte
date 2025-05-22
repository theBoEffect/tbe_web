<script lang="ts">
  import AboutContent from './AboutContent.svelte';
  import ProfessionalContent from './ProfessionalContent.svelte';
  import NewsContent from './NewsContent.svelte';
  import UEVContent from './UEVContent.svelte';
  import ContactContent from './ContactContent.svelte';
  
  export let title: string;
  export let bgColor: string;
  export let index: number;
  export let isExpanded: boolean;
  export let onToggle: (index: number) => void;
  export let hasExpandedColumn: boolean;

  // Determine if background is dark to set text color
  $: isDark = bgColor.toLowerCase() === '#000000';
  
  const baseClasses = "transition-all duration-500 ease-in-out flex flex-col items-center";

  // Background image handling for all columns
  $: backgroundImage = index === 0 ? 'thailand.jpeg' 
                    : index === 1 ? 'arizona.jpeg'
                    : index === 2 ? 'sahara.jpeg'
                    : index === 3 ? 'ww.jpeg'
                    : index === 4 ? 'mountain.jpeg'
                    : null;
                    
  // Different opacity for columns
  $: colorOpacity = index === 0 ? '45' 
                  : index === 1 ? '50'
                  : index === 2 ? '25'
                  : index === 3 && !isExpanded ? '85'
                  : index === 4 ? '75'
                  : null;

  // Special background positioning for column 4
  $: backgroundPosition = (index === 3 && isExpanded) ? 'center -200px' : 'center';
                    
  $: backgroundStyle = backgroundImage
    ? `
      background-image: url('/backgrounds/${backgroundImage}');
      background-size: cover;
      ${index === 3 ? 'background-position: var(--bg-position);' : 'background-position: center;'}
      background-repeat: no-repeat;
      ${colorOpacity ? `background-color: ${bgColor}${colorOpacity};` : ''}
      ${colorOpacity ? 'background-blend-mode: soft-light;' : ''}
    `
    : `background-color: ${bgColor};`;
</script>

<div
  class="h-full {baseClasses} cursor-pointer column-hover relative overflow-hidden"
  class:expanded={isExpanded}
  class:text-white={isDark}
  class:collapsed={!isExpanded && hasExpandedColumn}
  class:hoverable={!isExpanded}
  style="{backgroundStyle}"
  on:click={() => onToggle(index)}
  on:keydown={(e) => e.key === 'Enter' && onToggle(index)}
  role="button"
  tabindex="0"
>
  {#if index === 3}
    <div 
      class="mt-8 transition-all duration-300 title-wrapper {isExpanded ? 'self-start ml-8' : ''}"
      class:title-hidden={!isExpanded && hasExpandedColumn}
    >
      <div class="image-container">
        <img 
          src="/uev.png" 
          alt="UEV"
          class="h-8"
        />
      </div>
    </div>
  {:else}
    <h2 
      class="mt-8 text-2xl font-bold transition-all duration-300 title text-white {isExpanded ? 'self-start ml-8' : ''}"
      class:title-hidden={!isExpanded && hasExpandedColumn}
    >
      {title}
    </h2>
  {/if}
  
  {#if isExpanded}
    <div class="flex-1 w-full content-container">
      {#if index === 0}
        <AboutContent />
      {:else if index === 1}
        <ProfessionalContent />
      {:else if index === 2}
        <NewsContent />
      {:else if index === 3}
        <UEVContent />
      {:else if index === 4}
        <ContactContent />
      {/if}
    </div>
  {/if}
</div>

<style>
  /* Desktop styles */
  div {
    flex: 1;
    min-width: 0;
    transition: all 0.3s ease-in-out;
    --bg-position: center -200px;
  }

  .expanded {
    flex: 12;
    transition: all 0.5s ease-in-out;
    display: flex;
    flex-direction: column;
  }

  .content-container {
    overflow-y: auto;
    height: 100%;
    padding-bottom: 2rem;
  }
  
  .collapsed {
    flex: 0.1;
    min-width: 10px;
  }

  .title-hidden {
    opacity: 0;
    transform: scale(0.8);
    transition: all 0.3s ease-in-out;
  }

  .title,
  .image-container {
    position: relative;
    padding-bottom: 4px;
  }

  .title::after,
  .image-container::after {
    content: '';
    position: absolute;
    bottom: 0;
    left: 0;
    width: 0;
    height: 1px;
    background-color: #ff0054;
    transition: width 0.3s ease-in-out;
  }

  .column-hover:not(.expanded):hover .title::after,
  .column-hover:not(.expanded):hover .image-container::after {
    width: 100%;
  }

  .image-container {
    display: inline-block;
  }

  /* Mobile styles */
  @media screen and (max-width: 768px) {
    div {
      min-height: calc(100vh / 5);
      --bg-position: center;
      display: flex;
      flex-direction: column;
    }

    .expanded {
      min-height: auto;
      flex: 1;
      height: auto;
      padding-bottom: 2rem;
    }

    .content-container {
      overflow-y: auto;
      height: auto;
      min-height: 50vh;
      position: relative;
    }
    
    .collapsed {
      min-height: 40px;
      flex: 0;
    }

    /* Keep title visible and properly positioned in mobile */
    .expanded .title,
    .expanded .title-wrapper {
      opacity: 1 !important;
      transform: none !important;
      margin-bottom: 1rem;
      align-self: flex-start;
    }

    .expanded .title-hidden {
      opacity: 1 !important;
      transform: none !important;
    }
  }
</style> 