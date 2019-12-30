<script>
	import Navbar from './Navbar.svelte';
	import Player from './Player.svelte';
	import AddPlayer from './AddPlayer.svelte';

	let players = [
		{
			name: "John Doe",
			points: 53
		},
		{
			name: "Sam Smith",
			points: 45
		},
		{
			name: "Sara Wilson",
			points: 34
		},
	];

	const addPlayer = (e) => {
		const newPLayer = e.detail;
		players = [...players, newPLayer];
	}
	const removePlayer = e => {
		players = players.filter(player => player.name !== e.detail);
	}
</script>

<main>
	<Navbar/>
	<div class="container">
		<AddPlayer on:addplayer={addPlayer} />
		{#if players.length === 0}
			<p class="title has-text-centered">No Players</p>
		{:else}
			{#each players as player,i}
			<Player no={i+1} name={player.name} points={player.points} on:removeplayer={removePlayer} />
			{/each}
		{/if}
	</div>
</main>