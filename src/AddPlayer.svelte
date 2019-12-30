<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();
    
    let player = {
        name: "",
        points: 0
    }

    const onSubmit = e => {
        e.preventDefault();
        dispatch("addplayer", player);
        player = {
            name: "",
            points:0
        }
    }
</script>

<form on:submit={onSubmit}>
        <div class="field has-addons has-addons-centered">
            <div class="control">
                <input class="input" type="text" placeholder="Player name" bind:value={player.name}>
            </div>
            <div class="control">
                <input class="input" type="number" placeholder="Player points" bind:value={player.points}>
            </div>
            <div class="control">
                <input type="submit" class="button" value="Add Player">
            </div>
        </div>
</form>
<br>