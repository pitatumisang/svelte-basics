<script>

    import {createEventDispatcher} from 'svelte'

    const dispatch = createEventDispatcher()

    let player ={
        name:'',
        score:0
    }

    const onSubmit = (e) =>{
        e.preventDefault()
        dispatch('addplayer',player)
        
        player = {
            name:'',
            score:0
        }
    }
</script>


<div class="container">
    <form on:submit={onSubmit}>
        <input type="text" placeholder="Player name" bind:value={player.name}>
        <input type="number" bind:value={player.score}>

        <input class="btn" type="submit" value="Add Player" >
    </form>
</div>


<style>
    form{
        width: 100%;
        margin-bottom: 20px;
    }

    input{
        font-family: 'Montserrat', sans-serif;
    }
    input[type='text'],input[type='number']{
        padding: 5px 10px;
        border-radius: 3px;
        border:2px solid rgba(0,0,0,0.4);
    }

    input[type='text']:focus,input[type='number']:focus{
        outline: none;
        border:2px solid var(--primary-color);
            
    }

    input[type='submit']{
        background-color: var(--primary-color);
        color:var(--light-color);
        font-weight: 600;
        padding:0;
        padding: 8px 10px;
    }

    input[type='submit']:hover{
        background-color: #0b324d;
    }

</style>