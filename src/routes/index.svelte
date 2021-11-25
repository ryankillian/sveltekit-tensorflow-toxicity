<script>
	import * as toxicity from '@tensorflow-models/toxicity';

	import BadStuff from '$lib/BadStuff.svelte';
	import { insult, obscene, toxic } from '../stores/tweened';

	const threshold = 50;
	let model;
	let sample = '';
	let predictions;

	$: sentences = [sample];

	async function classify() {
		model = await toxicity.load(threshold);
		predictions = await model.classify(sentences);
	}

	function reset() {
		model = null;
		predictions = null;
		sample = '';
		$insult = 0;
		$obscene = 0;
		$toxic = 0;
	}
</script>

<div>
	<h2>Test here to check if your sentence is toxic.</h2>
	<textarea bind:value={sample} placeholder="Enter text" />
	<button on:click={classify}>Click to test</button>
	<button on:click={reset}> Reset</button>

	{#if predictions}
		<BadStuff {predictions} />
	{/if}
</div>

<style>
	div {
		display: grid;
		place-items: center;
	}
	textarea {
		margin: 10px;
	}
	button {
		margin: 10px;
	}
</style>
