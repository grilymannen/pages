<script>
	import { onMount } from 'svelte';
	// For src, "imgs/" is always added
	const widgetData = [
		{
			post: 'https://www.tumblr.com/slugfishh/734075615509086208/sait',
			src: 'sait.jpg',
			artist: 'slugfishh'
		},
		{
			post: 'https://www.tumblr.com/rain-mantis/798154938937212928/i-finally-tried-out-wigglypaint-its-very-fun-but',
			src: 'saint_wigglypaint.webp',
			artist: 'rain-mantis'
		},
		{
			post: 'https://x.com/ongomato/status/1510717248742342666',
			src: 'saint_circle.jpg',
			artist: 'Ongomato'
		}
	];

	let increment = 0;
	let rotation = $state({ x: 0, y: 0 });
	let yOffset = $state(0);
	let currentWidget = widgetData[2];

	onMount(() => {
		startBreathe();

		const widget = document.getElementById('widget');
		widget.addEventListener('mousemove', handleMouseMove);
		widget.addEventListener('mouseleave', handleMouseLeave);
	});
	function handleMouseLeave() {
		rotation.x = 0;
		rotation.y = 0;
	}
	function handleMouseMove(event) {
		const maxDegrees = 25; // This is what looks good
		const widget = event.originalTarget;
		const size = { height: widget.clientHeight, width: widget.clientWidth };
		const ratioX = event.layerX / size.width;
		const ratioY = event.layerY / size.height;
		rotation.x = Math.sin(ratioX - 0.5) * maxDegrees;
		rotation.y = Math.sin(ratioY - 0.5) * maxDegrees;
	}
	function startBreathe() {
		setInterval(animateBreathing, 1);
	}
	/*
  function endBreathe() {
    clearInterval(interval);
  }
  */
	function animateBreathing() {
		increment++;
		yOffset = Math.sin(increment * 0.02) * 5;
	}
</script>

<main class="grid h-screen w-screen grid-rows-[50px_1fr_50px] *:text-neutral-200">
	<div></div>
	<div class="flex h-full items-center justify-center gap-16">
		<h1 class="gulp w-80 text-4xl font-bold" aria-label="Hello, I am grily!"></h1>
		<div class="w-80 perspective-distant">
			<div
				class="relative hover:scale-110 hover:*:opacity-100"
				id="widget"
				style="top: {yOffset}px; 
          transition: all 0.1s; 
          transform: rotateX({rotation.y}deg) rotateY({rotation.x}deg);"
			>
				<img src={'imgs/' + currentWidget.src} alt="main widget" />
				<a
					href={currentWidget.post}
					class="absolute top-1 w-full bg-black/30 text-center text-blue-300 underline opacity-0 transition-opacity"
					target="_blank"
					rel="external"
					>↳ from @{currentWidget.artist}
				</a>
			</div>
		</div>
	</div>
	<div></div>
</main>

<style>
	.gulp::before {
		content: '';

		animation: animate-content 4s ease-in-out 1 forwards;
	}
	.gulp::after {
		content: '█';

		animation: blinky 1.3s infinite 1s;
	}
	@keyframes blinky {
		50% {
			content: '';
		}
	}
	@keyframes animate-content {
		0% {
			content: '';
		}
		5% {
			content: 'H';
		}
		10% {
			content: 'He';
		}
		15% {
			content: 'Hel';
		}
		20% {
			content: 'Hell';
		}
		25% {
			content: 'Hello';
		}
		30% {
			content: 'Hello,';
		}
		35% {
			content: 'Hello, ';
		}
		40% {
			content: 'Hello, I';
		}
		45% {
			content: 'Hello, I ';
		}
		50% {
			content: 'Hello, I a';
		}
		55% {
			content: 'Hello, I am';
		}
		60% {
			content: 'Hello, I am ';
		}
		65% {
			content: 'Hello, I am g';
		}
		70% {
			content: 'Hello, I am gr';
		}
		75% {
			content: 'Hello, I am gri';
		}
		80% {
			content: 'Hello, I am gril';
		}
		85% {
			content: 'Hello, I am grily';
		}
		90% {
			content: 'Hello, I am grily!';
		}
		100% {
			content: 'Hello, I am grily!';
		}
	}
</style>
