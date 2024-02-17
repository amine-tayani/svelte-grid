<script>
	import Header from './Header.svelte';
	import '../styles.css';

	let count = 0;

	function increment() {
		count++;
	}
</script>

<svelte:head>
	<title>Home page</title>
	<meta name="description" content="Svelte Home page" />
</svelte:head>

<Header />
<section>
	<h1>SvelteKit app</h1>
	<button disabled={count >= 10} on:click={increment} class="btn"> counter </button>
	<span>{count}</span>
	{#if count >= 10}
		you've reached the maximum counter click allowance
	{/if}
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	h1 {
		font-size: 4rem;
		letter-spacing: 0.134rem;
		text-align: center;
		width: 100%;
		padding: 80px 0px;
	}
	.btn {
		background-color: rgba(63, 61, 61, 0.8);
		border: none;
		padding: 10px 20px;
		font-size: 20px;
		font-weight: 600;
		color: var(--text-primary);
		border-radius: 8px;
		cursor: pointer;
		margin-bottom: 20px;
	}

	.btn:hover {
		background-color: rgba(63, 61, 61, 0.5);
	}
	.btn:disabled {
		cursor: not-allowed;
		opacity: 20%;
	}
</style>
