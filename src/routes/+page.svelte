<script>
	import PhotoGrid from '$lib/components/PhotoGrid.svelte';

	// Example photo data
	const photoData = [
		{
			id: '1',
			title: 'Mountain Vista',
			category: 'Landscape',
			imageUrl: '/images/20250412-DSC01418.jpg',
			altText: 'Mountain landscape at sunset'
		},
		{
			id: '2',
			title: 'Golden Hour Portrait',
			category: 'Portrait',
			imageUrl: '/images/20250412-DSC01416.jpg',
			altText: 'Portrait of a woman in golden hour lighting'
		},
		{
			id: '3',
			title: 'City Lights',
			category: 'Urban',
			imageUrl: '/images/20250412-DSC01326.jpg',
			altText: 'City skyline at night with lights'
		},
		{
			id: '4',
			title: 'Spring Bloom',
			category: 'Nature',
			imageUrl: '/images/20250412-DSC01283.jpg',
			altText: 'Macro photography of a flower in bloom'
		},
		{
			id: '5',
			title: 'Coastal Sunset',
			category: 'Landscape',
			imageUrl: '/images/20250412-DSC01254.jpg',
			altText: 'Sunset over the ocean'
		},
		{
			id: '6',
			title: 'Street Life',
			category: 'Urban',
			imageUrl: '/images/20250301-DSC00876.jpg',
			altText: 'Street photography of urban life'
		}
	];

	// Function to handle photo clicks
	function handlePhotoClick(photo) {
		console.log('Photo clicked:', photo.title);
		// You could navigate to a detail page or open a lightbox
		// e.g., goto(`/photos/${photo.id}`);
	}
</script>

<h1>Featured Photography</h1>

<PhotoGrid
	photos={photoData}
	onPhotoClick={handlePhotoClick}
	gridGap="24px"
/>