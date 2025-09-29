<script>
    let todos = $state([
        { id:1, text: 'Todo 1', checked: false},
		{ id:2, text: 'Todo 2', checked: false},
		{ id:3, text: 'Todo 3', checked: true},
		{ id:4, text: 'Todo 4', checked: false}
    ]);
</script>

<ul>
    {#each todos as todo}
    {@const { id, checked, text} = todo}
    <li>
        <input type="checkbox" name={text} {checked}>
        <span>{text}</span>
    </li>
        
    {/each}
</ul>