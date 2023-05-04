<script>
	import { Router, Route, Link } from "svelte-navigator";
	import Thermals from './components/Thermals.svelte'
	import Loads from './components/Loads.svelte'
	import Cooling from './components/Cooling.svelte'
	import ClocksExpanded from './components/ClocksExpanded.svelte'
	import Power from './components/Power.svelte'
	import Clocks from './components/Clocks.svelte'
</script>

<Router primary={false}>
	<header>

		<h1>Personal Terminal</h1>
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
					<h2>ram</h2>
				</div>
				<div class="col">
					<h2>thermals</h2>
					<Thermals/>
					<h2>voltages</h2>
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

	main {
		padding: 0;
		margin: 0 auto;
		
	}

	.grid {
		display: grid;
  	grid-template-columns: repeat(3, 1fr);
		grid-gap: 10px;
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
		text-align: center;
	}

	.col{
		/* border: 1px solid yellow */
	}
</style>