<script>
	import Counter from './Counter.svelte';
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcome_fallback from '$lib/images/svelte-welcome.png';
	import {spring, tweened} from 'svelte/motion';
	import Pie from './Pie.svelte';

	let percent = 0;
	const store = tweened(0, {duration: 1000});
	//const store = spring(0, {stiffness: 0.3, damping:0.3});
	$: store.set(percent);
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<h1>
		<span class="welcome">
			<picture>
				<source srcset={welcome} type="image/webp" />
				<img src={welcome_fallback} alt="Welcome" />
			</picture>
		</span>

		to my<br > <em>website</em>
	</h1>

	<h2>
		<em>TODO:<br>
			-Add drop down box<br>
			-Set pie chart to update with counter</em>
	</h2>

	<label>
		Percent
		<input type="number" min = "0" max="100" bind:value={percent}>
	</label>
	<Pie size = {200} percent={$store}/>
	<Counter />

	<h3> <em>Check out my <strong><a href = "https://github.com/mpanks">GitHub</a></strong></em></h3>
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
		width: 100%;
	}

	.welcome {
		display: block;
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}
</style>
