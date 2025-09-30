<script lang="ts">
	let clip = 'video.mp4'
	let currentTime = $state(0)
	let duration = $state(0)
	let paused = $state(true)
</script>

<div class="container">
	<!-- svelte-ignore a11y_media_has_caption -->
	<video src={clip} bind:currentTime bind:duration bind:paused></video>

	<div class="controls">
		<button onclick={() => paused = !paused}>
			{paused ? '▶️' : '⏸️'}
		</button>
		<span>{currentTime.toFixed(1)}/{duration.toFixed(1)}</span>
		<input type="range" bind:value={currentTime} max={duration} step={0.1} />
	</div>
</div>

<style>
	.container {
	  width: 600px;

		video {
			width: 100%;
			border-radius: 0.5rem;
		}

		.controls {
			display: flex;
			gap: 0.5rem;

			input[type="range"] {
				flex-grow: 1;
			}
		}
	}
</style>