<script lang="ts">
  import type { Photo } from '$lib/types/Photo';

  /** The photo object with all photo data */
  export let photo: Photo;
  
  /** Function to handle when this photo is clicked */
  export let onClick: (photo: Photo) => void = () => {};
</script>

<div
  class="photo-frame"
  on:click={() => onClick(photo)}
  on:keydown={(e) => {
    if (e.key === 'Enter' || e.key === ' ') onClick(photo);
  }}
  tabindex="0"
>
  <div class="photo-container">
    <img src={photo.imageUrl} alt={photo.altText} loading="lazy" />
    <div class="photo-overlay">
      <div class="text-container">
        <div class="text-backdrop"></div>
        <div class="photo-info">
          <h3>{photo.title}</h3>
          <span class="category">{photo.category}</span>
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  .photo-frame {
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    cursor: pointer;
    position: relative;
  }

  .photo-frame:hover, .photo-frame:focus {
    transform: translateY(-5px);
    box-shadow: 0 8px 12px rgba(0, 0, 0, 0.15);
  }

  .photo-container {
    position: relative;
    width: 100%;
    overflow: hidden;
  }

  .photo-container img {
    width: 100%;
    display: block;
    object-fit: cover;
  }

  .photo-overlay {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    padding: 20px;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    height: 100%;
    pointer-events: none;
  }

  .text-container {
    position: relative;
    align-self: flex-start;
    display: inline-block;
    border-radius: 4px;
    overflow: hidden;
    opacity: 0;
  }

  .text-backdrop {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.4);
    backdrop-filter: blur(8px);
    -webkit-backdrop-filter: blur(8px);
    z-index: 1;
    transition: opacity 0.3s ease;
  }

  .photo-info {
    position: relative;
    z-index: 2;
    padding: 10px 15px;
  }

  .photo-frame:hover .text-container,
  .photo-frame:focus .text-container {
    opacity: 1;
    transform: translateY(0);
  }
  
  .photo-info h3 {
    margin: 0 0 8px 0;
    font-size: 1.4rem;
    color: white;
    text-shadow: 1px 1px 3px rgba(0,0,0,0.3);
  }
  
  .category {
    font-size: 0.9rem;
    color: white;
    text-transform: uppercase;
    opacity: 0.9;
  }
</style>