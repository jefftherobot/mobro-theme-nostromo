<script>
	import { Router, Route, Link } from "svelte-navigator";
	import Thermals from './components/Thermals.svelte'
	import Loads from './components/Loads.svelte'
	import Cooling from './components/Cooling.svelte'
	import ClocksExpanded from './components/ClocksExpanded.svelte'
	import Power from './components/Power.svelte'
	import Clocks from './components/Clocks.svelte'
	import Memory from './components/Memory.svelte'
	import Voltages from './components/Voltages.svelte'
</script>

<Router primary={false}>
	<header>

		<h1>*(pyoutput     ver/1234393.1</h1>
		<hr/>

	</header>
	<main>
		<Route path="clocks" component={ClocksExpanded} />
		<Route>
			<div class="grid">
				<div class="col">
					<h2>loads</h2>
					<Loads/>
					<Power/>
					<h2>memory</h2>
					<Memory/>
				</div>
				<div class="col">
					<h2>thermals</h2>
					<Thermals/>
					<!-- <h2>voltages</h2>
					<Voltages/> -->
				</div>
				<div class="col">
					<h2>cooling</h2>
					<Cooling/>
					<Link to="clocks"><h2>clocks</h2>
						<Clocks/>
					</Link>
				</div>
			</div>
		</Route>
	</main>

</Router>

<style>
	header{
		margin: 0;
		grid-column: span 3;
		text-align: center;
	}


	main {
		padding: 0;
		margin: 0 auto;
		
	}

	.grid {
		display: grid;
  	grid-template-columns: repeat(3, 1fr);
		grid-gap: 0px;
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

	h2 {
		margin: 5px 0 0;
		font-size: 1.1em;
		font-weight: bold;
		border: 1px solid yellow;
		width: auto;
		display: inline-block;
		padding: 2px 4px;
	}

	.col{
		padding: 5px;
		border: 1px solid yellow;
	}

	.col:nth-child(2){
		border-left: 0;
		border-right: 0;
	}
</style>