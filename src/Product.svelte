<script>
    import {createEventDispatcher} from 'svelte';
    export let title;
    export let price;
    const dispatch = createEventDispatcher();
    function addToCart() {
        dispatch('add-to-cart','p1');
    }
</script>
<article>
    <h1>{title}</h1>
    <h2>{price}</h2>
    <button on:click="{addToCart}">Add to Cart</button>
    <button on:click="{()=>{dispatch('delete','p1')}}">Delete</button>
</article>