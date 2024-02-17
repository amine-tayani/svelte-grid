<script lang="ts">
	import Grid from './Grid.svelte';
	import { levels, type Level } from './levels';

	const easyLevel = levels[0];
	const create_grid = (level: Level) => {
		const shadowEmojis = level.emojis.slice();
		const pairs: string[] = [];
		for (let i = 0; i < level.size ** 2 / 2; i++) {
			const index = Math.floor(Math.random() * shadowEmojis.length);
			const emoji = shadowEmojis[index];
			shadowEmojis.slice(index, 1);
			pairs.push(emoji);
		}
		pairs.push(...pairs);
		return pairs;
	};

	let size: number = easyLevel.size;
	let grid: string[] = create_grid(easyLevel);
	let found: string[] = [];
</script>

<div>
	<div class="game">
		<div class="info"></div>
		<div class="grid-container">
			<Grid
				{grid}
				on:found={(e) => {
					found = [...found, e.detail.emoji];
				}}
				{found}
			/>
		</div>
		<div class="info"></div>
	</div>
</div>

<style>
	.game {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 100%;
	}
	.info {
		width: 80vmin;
		height: 10vmin;
		background-color: rgb(51, 53, 53);
	}
	.grid-container {
		width: 80vmin;
		height: 80vmin;
		background-color: purple;
	}
</style>
