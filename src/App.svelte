<script>

	import  Header from './Header.svelte'
	import Player from './Player.svelte';
	import AddPlayer from './AddPlayer.svelte'
	import Alert from './Alert.svelte'

	let players = [
		{	
			name:'Tumisang',
			score:200
		},
		{	
			name:'Bafokeng',
			score:300
		},
		{	
			name:'Tumelo',
			score:500
		}
	]

	let success;
	let msg;
	let isActive = false;

	const showAlert = () =>{
		isActive = true;
		setTimeout(() => {
			isActive = false
		}, 2000);
	}

	const addPlayer = (e) =>{
		const newPlayer = e.detail;

		showAlert();

		if (e.detail.name === '') {
			success =false;
			msg = `Please enter player's name`;
			
		}else{
			players = [...players,newPlayer]
			success = true;
			msg = 'Player added successfully!'
		}
	}

	const removePlayer = (e)=>{
		players = players.filter(player=> e.detail !== player.name)
		success = true;
		msg = 'Player romoved!'
		showAlert()
		
	}

</script>

<Header/>
<AddPlayer on:addplayer={addPlayer}/>

<section class="container">

	{#if isActive}
		<Alert success={success} alertMsg={msg}/>	
	{/if}

	{#if players.length === 0}
		<h3>No Players</h3>
	{:else}
		{#each players as player}
			<Player name={player.name} score={player.score} on:removeplayer={removePlayer}/>	
		{/each}
	{/if}
	
</section>

<style>


</style>