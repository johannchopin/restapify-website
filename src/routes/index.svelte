<script>
	import { vs2015 } from 'svelte-highlight/styles'
	import Header from '../components/Header.svelte'
	import Features from '../components/Features.svelte'
	import GettingStarted from '../components/GettingStarted.svelte'
</script>

<style>
	h1, figure, p {
		text-align: center;
		margin: 0 auto;
	}

	h1 {
		font-size: 2.8em;
		text-transform: uppercase;
		font-weight: 700;
		margin: 0 0 0.5em 0;
	}

	figure {
		margin: 0 0 1em 0;
	}

	img {
		width: 100%;
		max-width: 400px;
		margin: 0 0 1em 0;
	}

	p {
		margin: 1em auto;
	}

	#home {
		height: 100%;
		overflow: auto;
	}
</style>

<svelte:head>
	<title>Restapify</title>
	{@html vs2015}
</svelte:head>

<div id="home">
	<Header />
	<section class="container my-5 py-5">
		<Features />
		<hr />
		<GettingStarted />
	</section>
</div>
