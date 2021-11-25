<script>
	export let title;
	export let amount;
</script>

<div style="transform:translateX({amount * 100}px)">
	{title}
</div>

<style>
	div {
		display: grid;
		place-items: center;
		margin-top: 20px;
		height: 100px;
		width: 100px;
		background-color: #999;
	}
</style>
