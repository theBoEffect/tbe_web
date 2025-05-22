<script lang="ts">
  import InteractiveColumn from '$lib/components/InteractiveColumn.svelte';
  import { writable } from 'svelte/store';

  const columns = [
    { title: 'ABOUT', bgColor: '#00fff2', bgHoverColor: '#10b5b0' },       // Super Bright Cyan
    { title: 'PROFESSIONAL', bgColor: '#ff9500', bgHoverColor: '#d67520' }, // Bright Orange
    { title: 'NEWS', bgColor: '#00f6ff', bgHoverColor: '#009ecc' },        // Electric Blue
    { title: 'UEV', bgColor: '#000000', bgHoverColor: '#1A1A1A' },         // Black
    { title: 'CONTACT', bgColor: '#ffffff', bgHoverColor: '#E8E8E8' }      // Pure White
  ];

  let expandedIndex = -1;

  function handleToggle(index: number) {
    expandedIndex = expandedIndex === index ? -1 : index;
  }

  $: hasExpandedColumn = expandedIndex !== -1;
</script>

<div class="flex md:flex-row flex-col h-screen w-full overflow-hidden">
  {#each columns as column, i}
    <InteractiveColumn
      title={column.title}
      bgColor={column.bgColor}
      index={i}
      isExpanded={expandedIndex === i}
      hasExpandedColumn={hasExpandedColumn}
      onToggle={handleToggle}
    />
  {/each}
</div>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
    overflow: hidden;
  }

  /* Ensure the container takes up full width and height */
  div {
    width: 100vw;
    height: 100vh;
  }
</style> 