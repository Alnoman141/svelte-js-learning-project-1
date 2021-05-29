<main>
    <h1>{greeting} {name}. {message}</h1>
    <!-- <input type="text" bind:value={name} on:keypress={nameChangeEvent} /> -->
    <input type="text" bind:value={name}  />

</main>
<script>
    // import { createEventDispatcher } from 'svelte';
    // let dispatcher = createEventDispatcher();
    export let name = 'Shamsia Ferdous Pia';
	export let greeting;
    export let message;

    // function nameChangeEvent(e){
    //     if(e.key === 'Enter'){
    //         dispatcher('nameChange', name);
    //     }
    // }
</script>

<style>
    main > h1 {
		font-size: 50px;
		text-align: center;
		font-weight: bolder;
	}
</style>