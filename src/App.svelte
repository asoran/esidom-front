<script lang="typescript">
	import { onMount } from "svelte";
	import {} from "../public/mock.json";
	import Lamp from "./Lamp.svelte";
	import Sensor from "./Sensor.svelte";
	
	export let name: string;

	let count: number = 0;
	onMount(() => {
		const interval = setInterval(() => count++, 1000);
		return () => {
			clearInterval(interval);
		};
	});
</script>

<style>
	:global(body) {
		margin: 0;
		font-family: Arial, Helvetica, sans-serif;
		background-color: #120639;
	}

	/*
	div code {
		background: #0002;
		padding: 4px 8px;
		border-radius: 4px;
	}
	div p {
		margin: 0.4rem;
	}

	div header {
		background-color: #f9f6f6;
		color: #333;
		min-height: 100vh;
		font-size: calc(10px + 2vmin);
	}
	div a {
		color: #ff3e00;
	}
	div img {
		height: 36vmin;
		margin-bottom: 3rem;
		animation: App-logo-spin infinite 1.6s ease-in-out alternate;
	}
	@keyframes App-logo-spin {
		from {
			transform: scale(1);
		}
		to {
			transform: scale(1.06);
		}
	}*/
</style>

<main>
	<div>	
		<div class="grid grid-flow-col grid-rows-2 grid-cols-4 mt-4 ml-4">
			<div>
				<Lamp />
			</div>
			<div class= "row-start-1 col-start-2">
			<Sensor />
			</div>
		</div>
		<div class = "absolute bottom-0 right-0 h-16 w-16">
			<button 
			class="py-2 px-4 bg-blue-400  text-white text-xl font-semibold rounded-full shadow-md hover:bg-blue-500 focus:outline-none absolute" 
			type="button"> + </button>
		</div>
	</div>


	<!--
	<figure
		class="md:flex bg-gradient-to-tr from-yellow-200 to-purple-600 rounded-xl p-8 md:p-0">
		<img
			class="hover:bg-blue-500 w-32 h-32 md:w-48 md:h-auto md:rounded-none rounded-full mx-auto bg-red-500"
			src="/favicon.png"
			alt=""
			width="384"
			height="512" />
		<div class="pt-6 md:p-8 text-center md:text-left space-y-4">
			<blockquote>
				<p class="text-lg font-semibold">
					“Tailwind CSS is the only framework that I've seen scale on
					large teams. It’s easy to customize, adapts to any design,
					and the build size is tiny. Yo comment tu vas ?”
				</p>
			</blockquote>
			<figure>
				<figcaption class="font-medium">
					<div class="text-cyan-600">
						{name}
						il y a
						{count}
						secondes
					</div>
				</figcaption>
			</figure>
		</div>
	</figure>
	-->
</main>
