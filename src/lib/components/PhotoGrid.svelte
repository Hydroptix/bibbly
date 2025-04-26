<script lang="ts">
  import PhotoFrame from './PhotoFrame.svelte';
  import type { Photo } from '$lib/types/Photo';

  /** Array of photo objects */
  export let photos: Photo[] = [];
  
  /** Function to handle when a photo is clicked */
  export let onPhotoClick: (photo: Photo) => void = () => {};
  
  /** Gap between grid items */
  export let gridGap: string = '0px';
</script>

<div class="masonry-layout" style="--column-gap: {gridGap}; --item-gap: {gridGap};">
  {#each photos as photo (photo.id)}
    <div class="masonry-item">
      <PhotoFrame {photo} onClick={onPhotoClick} />
    </div>
  {/each}
</div>

<style>
  .masonry-layout {
    column-count: 1;
    column-gap: var(--column-gap);
    width: 100%;
  }
  
  @media (min-width: 1024px) {
    .masonry-layout {
      column-count: 2;
    }
  }
  
  @media (min-width: 1536px) {
    .masonry-layout {
      column-count: 3;
    }
  }
  
  .masonry-item {
    display: inline-block;
    width: 100%;
    margin-bottom: var(--item-gap);
    break-inside: avoid;
  }
</style>