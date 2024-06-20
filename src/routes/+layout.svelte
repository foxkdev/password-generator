<script>
	import './styles.css';
</script>

<div class="w-full h-full bg-gray-800">
	<main>
		<slot />
	</main>

	<footer class="flex text-white justify-center w-full">
		<p class="text-lg">Desarrollado con SvelteKit por <a class="font-semibold" href="https://github.com/foxkdev">@Foxkdev</a></p>
	</footer>
</div>
