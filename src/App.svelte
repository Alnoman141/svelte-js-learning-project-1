<main>
	<!-- <Hello on:nameChange={nameChanged} message={message} name={name} greeting={greeting}/> -->
	<Hello message={message} bind:name={name} greeting={greeting}/>
	<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Neque, temporibus, soluta cumque ratione similique voluptatibus laboriosam tempore voluptate explicabo doloribus nesciunt nisi corporis quae voluptatum labore, eveniet porro dolor nobis autem repellendus suscipit. Nobis molestiae itaque, ipsum quasi delectus suscipit expedita doloribus eveniet deleniti ad, fugiat quos. Doloribus incidunt dolorum quidem perspiciatis ipsam, aliquam, est dolore omnis quibusdam alias fugiat consequuntur consequatur neque aperiam quaerat impedit explicabo. </p>
	<h2>{name}</h2>
</main>
<script>
	import Hello from "./Hello.svelte";
	let name = 'Abdullah Al Noman';
	let greeting = "Hello!";
	let message = "Your Are Welcome To The Svelte World.";

	// function nameChanged(e){
	// 	name = e.detail;
	// }
</script>
<style type="text/css">
	main {
		width: 1170px;
		margin: 0 auto;
		background-color: #ddd;
		padding: 20px;
		box-sizing: border-box;
	}

	
	main > p {
		font-size: 30px;
	}
</style>