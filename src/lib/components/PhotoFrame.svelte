<script lang="ts">
  import type { Photo } from '$lib/types/photo';

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
      <div class="text-backdrop"></div>
      <div class="photo-info">
        <h3>{photo.title}</h3>
        <span class="category">{photo.category}</span>
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
    transition: opacity 0.3s ease;
    padding: 20px;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    height: 100%;
    pointer-events: none;
  }
  
  .text-backdrop {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    height: auto;
    padding-top: 100px;
    background: linear-gradient(to top, 
      rgba(0,0,0,0.4) 0%, 
      transparent 100%);
    backdrop-filter: blur(8px);
    -webkit-backdrop-filter: blur(8px);
    z-index: 1;
    opacity: 0;
    transition: opacity 0.3s ease;
  }

  .photo-info {
    position: relative;
    z-index: 2;
    opacity: 0;
    transition: opacity 0.3s ease, transform 0.3s ease;
    transform: translateY(10px);
  }
  
  .photo-frame:hover .photo-info,
  .photo-frame:focus .photo-info {
    opacity: 1;
    transform: translateY(0);
  }
  
  .photo-frame:hover .text-backdrop,
  .photo-frame:focus .text-backdrop {
    opacity: 1;
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