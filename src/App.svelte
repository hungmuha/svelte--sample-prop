<script>
	import Product from './Product.svelte';
	import Modal from './Modal.svelte';

	let products = [
		{
			id:"p1",
			title:'A book',
			price: 9.99
		}
	];

	let showModal = false;
	let closable = false;

	function addToCart(event) {
		console.log(event);
	}

	function deleteProduct(event) {
		console.log(event);
	}
</script>

{#each products as product}
<Product 
	{...product}
	on:add-to-cart={addToCart}
	on:delete={deleteProduct}/>
{/each}
<button on:click="{()=>(showModal = true)}">show Modal</button>
{#if showModal}
<Modal 
	on:cancel="{()=>(showModal= false)}" 
	on:close="{()=>(showModal= false)}"
	let:didAgree = {closable}>
	<h1 slot="header">Hi!</h1>
	<h2>This works!!</h2>
	<button slot="footer" on:click="{()=>showModal=false}" disabled={!closable}>Confirm</button>
</Modal>
{/if}