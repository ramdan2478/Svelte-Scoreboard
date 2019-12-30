<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();
    
    export let no;
    export let name;
	export let points;
	let showControls = false;

	const addPoint = () => (points += 1);
	const removePoint = () => (points -= 1);
    const toggleControls = () => (showControls = !showControls);
    const removePlayer = () => dispatch("removeplayer", name);
</script>

<main>
    <div class="card">
        <header class="card-header">
            <p class="card-header-title">
            {no}. {name}
            </p>
            <button class="button is-large" on:click={toggleControls}>
				{#if showControls}-{:else}+{/if}
			</button>
            <button class="button is-large is-danger" on:click={removePlayer}>x</button><br>
        </header>
        <div class="card-content">
            <div class="content">
            Name : {name}<br/>
            Points : {points}
            </div>
            {#if showControls}

            <div class="field has-addons">
            <div class="control">
                <input class="input" type="number" bind:value={points}>
            </div>
            <div class="control">
                <button class="button" on:click={addPoint}>+1</button>
            </div>
            <div class="control">
			    <button class="button is-dark" on:click={removePoint}>-1</button>
            </div>
            </div>

			
			{/if}
        </div>
    </div>
</main>

<style>
	main {
		/* text-align: center; */
		/* padding: 1em; */
		max-width: 510px;
		margin: 0 auto;
	}

	.card-header-title {
		color: #ff3e00;
	}
</style>