<script>
	import { Router, Route, Link } from "svelte-navigator";
	import Thermals from './components/Thermals.svelte'
	import Loads from './components/Loads.svelte'
	import Fans from './components/Fans.svelte'
	import Clocks from './components/Clocks.svelte'
</script>

<Router>
	<header>

		<h1>Personal Terminal</h1>
		<hr/>

	</header>
	<main>
		<Route path="clocks" component={Clocks} />
		<Route path="/">
			<div class="grid">
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
					<Link to="clocks"><h2>clocks</h2>
					<!-- <Clocks/> -->
					</Link>
				</div>
				<div class="block">
					<h2>power</h2>
				</div>
				<div class="block">
					<h2>ram</h2>
				</div>
			</div>
		</Route>
	</main>

</Router>

<style>

	main {
	
		text-align: center;
		padding: 0;
		margin: 0 auto;
		height: 100%;
		width:100% ;
	}

	.grid {
		display: grid;
  	grid-template-columns: repeat(3, 1fr);
		grid-template-rows: auto repeat(2, 1fr);
		grid-gap: 20px;
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

	header{
		margin: 0 0 10px;
		grid-column: span 3;
	}

	.block{
		/* border: 1px solid yellow */
	}
</style>