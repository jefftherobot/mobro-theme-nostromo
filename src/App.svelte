<script>
	import Thermals from './components/Thermals.svelte'
	import Loads from './components/Loads.svelte'
	import Fans from './components/Fans.svelte'
	import Clocks from './components/Clocks.svelte'
</script>

<main>
	<div class="title-row">
		<h1>Personal Terminal</h1>
		<hr/>
	</div>
		
	<div class="block loads-block">
		<h2>loads</h2>
		<Loads/>
	</div>
	<div class="block">
		<h2>thermals</h2>
		<Thermals/>
	</div>
	<div class="block">
		<h2>fans</h2>
		<Fans/>
	</div>
	<div class="block">
		<h2>clocks</h2>
		<!-- <Clocks/> -->
	</div>
	<div class="block">
		<h2>power</h2>
	</div>
	<div class="block">
		<h2>ram</h2>
	</div>

</main>



<style>

	main {
		display: grid;
  	grid-template-columns: repeat(3, 1fr);
		grid-template-rows: auto repeat(2, 1fr);
		grid-gap: 20px;
		text-align: center;
		padding: 0;
		margin: 0 auto;
		height: 100%;
		width:100% ;
	}

	h1 {
		margin: 0;
		color: #000;
		text-transform: uppercase;
		font-size: 2em;
		line-height: .8;
		font-weight: 100;
		background: yellow;
	}

	.title-row{
		margin: 0 0 10px;
		grid-column: span 3;
	}

	.block{
		/* border: 1px solid yellow */
	}
</style>