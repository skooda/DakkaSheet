<script>
	import { page } from '$app/stores';
	import logo from '$lib/images/logo.svg';
	import github from '$lib/images/github.svg';
</script>

<header>
	<div class="corner">
		<img class="logo" src={logo} alt="Datasheet Generator" />
	</div>

	
	<div class="corner">
		<a href="https://github.com/sveltejs/kit">
			<img src={github} alt="GitHub" />
		</a>
	</div>
</header>

<style>
	header {
		display: flex;
		justify-content: space-between;
	}

	.corner a {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 100%;
	}
	
	.corner img {
		width: 4em;
		height: 4em;
		object-fit: contain;
	}

	.corner .logo {
		width: 9em;
		height: 4em;
		object-fit: contain;
	}


	path {
		fill: var(--background);
	}

	a:hover {
		color: var(--color-theme-1);
	}
</style>
