<script>
    export let success;
	export let alertMsg; 
	let alertType;

	if(success){
		alertType = 'success'
	}else{
		alertType = 'error'
	}

</script>

<div class="alert {alertType}" >{alertMsg}</div>

<style>
    .alert{
		border-radius: 4px;
		padding: 10px;
		font-size: 12px;
		font-weight: 700;
		margin-bottom: 10px;
		letter-spacing: 2px;
	}

	.success {
		background-color: #d4edda;
		border: 1px solid #c3e6cb;
		color: #155724;
	}

	.error{
		background-color: #f8d7da;
		border: 1px solid #f5c6cb;
		color: #721c24;
	}
</style>