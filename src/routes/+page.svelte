<script>
	import { setContext } from "svelte";
	import { browser } from "$app/environment";
	import Meta from "$components/Meta.svelte";
	import Index from "$components/Index.svelte";
	import copy from "$data/copy.json";
	import version from "$utils/version.js";

	let { data } = $props();

	version();

	const preloadFont = [
		"https://datazoba.com/assets/fonts/tiempos/TiemposTextWeb-Regular.woff2",
		"https://datazoba.com/assets/fonts/tiempos/TiemposTextWeb-Bold.woff2",
		"https://datazoba.com/assets/fonts/atlas/AtlasGrotesk-Regular-Web.woff2",
		"https://datazoba.com/assets/fonts/atlas/AtlasGrotesk-Bold-Web.woff2"
	];

	const metadata = copy.meta ?? copy;
	const { title, description, url, keywords } = metadata;
	setContext("copy", copy);
	setContext("data", data);
</script>

<Meta {title} {description} {url} {preloadFont} {keywords} />
<Index />
