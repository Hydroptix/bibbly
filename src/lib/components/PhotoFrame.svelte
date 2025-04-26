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
    color: white;
    opacity: 0;
    transition: opacity 0.3s ease;
    padding: 20px;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    height: 100%;
  }
  
  .photo-frame:hover .photo-overlay,
  .photo-frame:focus .photo-overlay {
    opacity: 1;
  }
  
  .photo-info {
    text-shadow: 3px 3px 3px rgba(0,0,0,1);
  }
  
  .photo-info h3 {
    margin: 0 0 8px 0;
    font-size: 1.4rem;
  }
  
  .category {
    font-size: 0.9rem;
    text-transform: uppercase;
    opacity: 0.9;
  }
</style>