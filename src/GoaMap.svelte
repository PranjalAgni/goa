<script lang="ts">
	import { onMount } from 'svelte';
	import L from 'leaflet';

	let map: L.Map;

	// Define marker data
	let markerData = [
		{
			lat: 15.50737993463446,
			lng: 73.80679972417467,
			name: 'Santa Terra 🏠',
			icon: '🏠',
			description: 'bnb where we stayed nice little 1BHK with pool 🏊‍♂️'
		},
		{
			lat: 15.500293025753603,
			lng: 73.79265456650396,
			name: 'Tereza Beach House',
			icon: '🍕',
			description: 'Amazing place on the beach side, food was okayish but good vibes'
		},
		{
			lat: 15.49725912788147,
			lng: 73.79970231068054,
			name: 'Carlitos',
			icon: '🍺',
			description: 'Awesome food and a quite chill place'
		},
		{
			lat: 15.54369469526764,
			lng: 73.81254865301062,
			name: 'Kismoor Sangolda',
			icon: '🍺',
			description: 'Nice place to have lunch and work at'
		},
		{
			lat: 15.616446680027133,
			lng: 73.7555000088352,
			name: 'Thalassa',
			icon: '🍺',
			description: 'Do you want to do crazy wild Goa party'
		},
		{
			lat: 15.616446680027133,
			lng: 73.7555000088352,
			name: 'Purple Martini',
			icon: '🍺',
			description:
				'Best sunset place with amazing food & ambience, we celebrated a friends birthday here and it was awesomeeee'
		}
	];

	onMount(() => {
		// Initialize the map
		map = L.map('map').setView([15.2993, 74.124], 10); // Goa coordinates and initial zoom level
		L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png').addTo(map); // Add OpenStreetMap tiles

		// Add markers to the map
		markerData.forEach((location) => {
			L.marker([location.lat, location.lng], {
				icon: L.divIcon({
					className: 'custom-marker-icon',
					html: `<span class="emojimarker">${location.icon}</span>` // Use emoji as marker icon
				})
			})
				.addTo(map)
				.bindPopup(`<b>${location.name}</b><br>${location.description}`)
				.openPopup();
		});
	});
</script>

<div id="map" class="map"></div>

/** Places candolim beach calungate beach santa terra carlitos */

<!-- GoaMap.svelte -->
<style lang="ts">
	@import 'leaflet/dist/leaflet.css';

	/* Add any additional custom styles here */
	.map {
		height: 100vh; /* Adjust the height as needed */
	}

	.custom-marker-icon {
		width: 60px;
		height: 60px;
		text-align: center;
	}

	.emojimarker {
		font-size: 34px;
	}
</style>
