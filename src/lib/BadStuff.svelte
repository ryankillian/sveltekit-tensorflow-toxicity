<script>
	import { insult, obscene, toxic } from '../stores/tweened';
	import BadThing from './BadThing.svelte';

	export let predictions;

	$insult = predictions[1].results[0].probabilities[1];
	$obscene = predictions[2].results[0].probabilities[1];
	$toxic = predictions[6].results[0].probabilities[1];
</script>

<BadThing title={predictions[1].label} amount={$insult} />
<BadThing title={predictions[2].label} amount={$obscene} />
<BadThing title={predictions[6].label} amount={$toxic} />
