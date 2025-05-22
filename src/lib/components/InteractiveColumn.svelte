<script lang="ts">
  export let title: string;
  export let bgColor: string;
  export let bgHoverColor: string;
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
    <div class="flex-1 flex items-center justify-center">
      <p class="text-3xl">hello world</p>
    </div>
  {/if}
</div>

<style>
  /* Default state - even distribution */
  div {
    flex: 1;
    min-width: 0; /* Allow shrinking below content size */
    transition: all 0.3s ease-in-out;
    --bg-position: center -200px;
  }

  /* Expanded state */
  .expanded {
    flex: 12; /* Take up more space when expanded */
    transition: all 0.5s ease-in-out;
  }
  
  /* Collapsed state - when another column is expanded */
  .collapsed {
    flex: 0.1; /* Very narrow when collapsed */
    min-width: 10px; /* Minimum width when collapsed */
  }

  /* Title visibility */
  .title-hidden {
    opacity: 0;
    transform: scale(0.8);
    transition: all 0.3s ease-in-out;
  }

  /* Title and image container styles */
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

  /* Hover effects for both title and image */
  .column-hover:not(.expanded):hover .title::after,
  .column-hover:not(.expanded):hover .image-container::after {
    width: 100%;
  }

  /* Image container specific styles */
  .image-container {
    display: inline-block;
  }

  /* Mobile styles */
  @media (max-width: 768px) {
    div {
      min-height: calc(100vh / 5); /* Even distribution in mobile */
      --bg-position: center; /* Reset background position for mobile */
    }

    .expanded {
      flex: 12;
      min-height: 60vh;
    }
    
    .collapsed {
      flex: 0.1;
      min-height: 40px;
    }
  }
</style> 