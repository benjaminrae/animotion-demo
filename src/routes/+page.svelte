<script lang="ts">
	import '../styles/app.css'
	import SlidesCard from '../components/SlidesCard.svelte'
</script>

<section class="p-8 h-full flex flex-col justify-center font-sans text-2xl">
	<h1 class="text-6xl mb-6">
		Slide decks
	</h1>
	<ul class="list-none flex flex-col gap-8">
		<SlidesCard location="/testing-library" title="Testing Library"
								description="Examples of how to use Testing Library in React" />
		<SlidesCard location="/example" title="Animotion Demo" description="Examples of how to use Animotion" />
	</ul>
</section>
