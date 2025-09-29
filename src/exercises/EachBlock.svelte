<script>
	let todos = $state([
		{ id:1, text: 'Todo 1', done: false},
		{ id:2, text: 'Todo 2', done: false},
		{ id:3, text: 'Todo 3', done: false},
		{ id:4, text: 'Todo 4', done: false}
	])

	$inspect(todos);
</script>

<ul>
	{#each todos as { id, text, done}, i (id)}
		<li>
			<input type="checkbox" checked={done} value={done} onclick={() => (todos[i].done = !done)}>
			<span style:color={done ? 'orangered' : ''}>{text}</span>
		</li>
		{:else}
		<p>No itmes</p>
	{/each}
</ul>