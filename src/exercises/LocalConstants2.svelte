<script lang="ts">
	let size = 600
	let tiles = 8
</script>

<svg width={size} height={size}>
	{#each Array(tiles), col}
		{#each Array(tiles), row}
			{@const tile = size / tiles}
			{@const x = col * tile}
			{@const y = row * tile}
			{@const width = tile}
			{@const height = tile}
			{@const fill = (col + row) % 2 === 0 ? 'orangered' : 'white'}
			<rect {x} {y} {width} {height} {fill} />
		{/each}
	{/each}
</svg>