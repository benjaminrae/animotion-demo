<script lang="ts">
	import StartSlides from './StartSlides.svelte'

	export let location: string
	export let title: string
	export let description: string
</script>


<li>
	<div class="mb-4">
		<h2 class="mb-4">{title}</h2>
		<p>{description}</p>
	</div>
	<StartSlides location={location} />
</li>