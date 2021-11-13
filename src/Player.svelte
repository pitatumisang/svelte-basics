<script>
    import {createEventDispatcher} from 'svelte'

    const dispatch = createEventDispatcher()
    
    export let name;
	export let score;

    let showControls = false;

	const subtractScore = ()=>{score -= 1}
	const addScore = ()=>{score += 1}
    const toggleControls = () =>{showControls = !showControls}


    const removePlayer = (e)=>{
        dispatch('removeplayer',name)
    }


</script>

<div>
    <h3>{name}</h3>
        <button class="btn" on:click={toggleControls}>
           {showControls ? 'hide':'show'}
        </button>

    <p>{score}</p>

    <button class="btn btn-remove" on:click={removePlayer}>Romove</button>

    {#if showControls}
        <button class="btn" on:click={subtractScore}> -1 </button>
        <button class="btn" on:click={addScore}> +1 </button>
    {/if}
</div>		

<style>

div{
    position: relative;
    background-color: #fff;
    padding:20px;
    margin-bottom: 10px;
    border-radius: 4px;
    box-shadow: 1px 1px 5px rgba(0, 0, 0, 0.3);
		
	}

	h3{
		margin-bottom: 10px;
        display: inline;
        margin-right: 10px;
	}

	p{
		font-weight: 500;
	}

    .btn-remove{
        position: absolute;
        top: 20px;
        right: 20px;
        background-color: var(--danger-color);
        color: var(--light-color);
    }

    .btn-remove:hover{
        background-color: #d40d21;
        color: #fff;
    }

</style>