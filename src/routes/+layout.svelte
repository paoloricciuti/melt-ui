<script lang="ts">
	import '@fontsource/inter/100.css';
	import INTER_100 from '@fontsource/inter/files/inter-latin-100-normal.woff2';
	import '@fontsource/inter/200.css';
	import INTER_200 from '@fontsource/inter/files/inter-latin-200-normal.woff2';
	import '@fontsource/inter/300.css';
	import INTER_300 from '@fontsource/inter/files/inter-latin-300-normal.woff2';
	import '@fontsource/inter/400.css';
	import INTER_400 from '@fontsource/inter/files/inter-latin-400-normal.woff2';
	import '@fontsource/inter/500.css';
	import INTER_500 from '@fontsource/inter/files/inter-latin-500-normal.woff2';
	import '@fontsource/inter/600.css';
	import INTER_600 from '@fontsource/inter/files/inter-latin-600-normal.woff2';
	import '@fontsource/inter/700.css';
	import INTER_700 from '@fontsource/inter/files/inter-latin-700-normal.woff2';
	import '@fontsource/inter/800.css';
	import INTER_800 from '@fontsource/inter/files/inter-latin-800-normal.woff2';
	import '@fontsource/inter/900.css';
	import INTER_900 from '@fontsource/inter/files/inter-latin-900-normal.woff2';

	import '../app.postcss';
	import '../fonts.css';

	import { dev } from '$app/environment';
	import { page } from '$app/stores';
	import { JsIndicator, SiteHeader, TailwindIndicator } from '$docs/components/index.js';
	import { cn } from '$docs/utils/index.js';

	import { ModeWatcher } from 'mode-watcher';

	$: isRoot = $page.url.pathname === '/';
</script>

<svelte:head>
	<link rel="preload" as="font" href={INTER_100} type="font/woff2" crossorigin="anonymous" />
	<link rel="preload" as="font" href={INTER_200} type="font/woff2" crossorigin="anonymous" />
	<link rel="preload" as="font" href={INTER_300} type="font/woff2" crossorigin="anonymous" />
	<link rel="preload" as="font" href={INTER_400} type="font/woff2" crossorigin="anonymous" />
	<link rel="preload" as="font" href={INTER_500} type="font/woff2" crossorigin="anonymous" />
	<link rel="preload" as="font" href={INTER_600} type="font/woff2" crossorigin="anonymous" />
	<link rel="preload" as="font" href={INTER_700} type="font/woff2" crossorigin="anonymous" />
	<link rel="preload" as="font" href={INTER_800} type="font/woff2" crossorigin="anonymous" />
	<link rel="preload" as="font" href={INTER_900} type="font/woff2" crossorigin="anonymous" />
</svelte:head>

<ModeWatcher defaultMode="dark" />

<a
	href="#main"
	class="force-dark fixed top-[-20rem] z-0 ml-56 rounded-br-xl rounded-tl-xl bg-neutral-900 px-2 py-1 text-neutral-100 focus:top-4 focus:z-[1000] max-sm:right-[6]"
	tabindex="0"
>
	Skip to main content
</a>
<div class="relative flex min-h-screen flex-col md:flex-col-reverse" id="page">
	<div class="flex flex-1">
		<slot />
	</div>
	<header
		class={cn(
			'sticky bottom-0 z-40 w-full px-2 pb-2 md:bottom-[none] md:top-0 md:pb-0 md:pt-2',
			!isRoot && 'bg-neutral-900'
		)}
	>
		<SiteHeader />
	</header>

	{#if dev}
		<TailwindIndicator />
		<JsIndicator />
	{/if}
</div>
