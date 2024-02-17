<script lang="ts">
	export let emoji: string;
	export let selected = false;
	export let found: boolean;
</script>

<div class="square" class:flipped={selected}>
	<button on:click>
		{#if !found}
			<span>{emoji}</span>
		{/if}
	</button>
</div>

<style>
	.square {
		background-color: blue;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	span {
		font-size: 2em;
		pointer-events: none;
	}
	button {
		position: relative;
		width: 100%;
		height: 100%;
	}
	.flipped button {
		background-color: tomato;
	}
</style>
