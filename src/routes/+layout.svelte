<script lang="ts">
	import '../app.css';
	let darkMode = $state(false);
	let { children } = $props();



	function toggleDarkMode() {
		darkMode = !darkMode;
		if (darkMode === true) {
			localStorage.theme = "dark";
		}
		else {
			localStorage.theme = "light";
		}
		document.documentElement.classList.toggle('dark', localStorage.theme === 'dark')

	}
</script>

<nav class="fixed flex items-center justify-between shadow-sm z-10 h-16 w-full px-2 bg-neutral-50 dark:bg-neutral-950 text-neutral-900 dark:text-neutral-200">
	<p class="text-xl">W.A.I.T</p>
	<button onclick={toggleDarkMode} aria-label="Toggle dark mode" aria-pressed={darkMode} class=" border rounded-lg border-neutral-500 hover:border-neutral-400 bg-moon-svg dark:bg-sun-svg size-12"></button>
</nav>
<nav
	aria-labelledby="lessons-header"
	class="fixed hidden h-screen w-80 flex-col bg-neutral-200 dark:bg-neutral-800 text-neutral-900 dark:text-neutral-200 px-2 pt-16 text-right md:flex"
>
	<h2 class="mt-14 text-2xl" id="lessons-header">Lessons</h2>
	<ul class="mt-8 flex flex-col gap-8 text-xl">
		<li>
			<a href="/lesson-1">Lesson 1: Keyboard Accessibility</a>
		</li>
		<li>
			<a href="/lesson-1">Lesson 2: ARIA 101</a>
		</li>
	</ul>
</nav>
<div class="flex justify-center bg-neutral-100 dark:bg-neutral-900 pt-32 text-neutral-900 dark:text-neutral-200 min-h-screen md:pl-80">
	{@render children()}
</div>
