<script>
	import FormulaInput from './FormulaInput.svelte';
	import Result from './Result.svelte';

	let data = {
		a: 0,
		b: 0,
		c: 0
	}


	function setValue(event) {
		let newData = {...data};
		newData[event.detail.id] = event.detail.value;
		data = newData;
	}

</script>

<style>
	.container {
		margin-top: 1rem;
	}

</style>


<div class="container">
	<FormulaInput 
		on:inputA="{setValue}"
		on:inputB="{setValue}"
		on:inputC="{setValue}"/>
	<Result data="{data}"/>
</div>
