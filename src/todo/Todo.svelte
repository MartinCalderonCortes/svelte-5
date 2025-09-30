<script lang="ts">
    import { slide } from "svelte/transition";

    let todo = $state('');
    let todos = $state([]);
    let remainTodos = $derived(remainingTodos())

    function addTodo(event: SubmitEvent) {
        event.preventDefault();
        todos.push({
            id: crypto.randomUUID(),
            text: todo,
            completed: false
        });
        todo = ''
    }

    function removeTodo(todo) {
        todos = todos.filter((currentTodo) => currentTodo.id !== todo.id);
        

    }

    function remainingTodos() {
        return todos.filter((todo) => !todo.completed).length
    }
</script>

<form onsubmit={addTodo}>
    <input type="text" placeholder="Add todo" bind:value={todo}>
</form>

<section>
    <ul>
        {#each todos as todo (todo)}
            <li transition:slide>
                <input type="checkbox" bind:checked={todo.checked}>
                <input type="text" bind:value={todo.text}>
                <button onclick={() => removeTodo(todo)}>X</button>
            </li>
        {/each}
    </ul>

    <div>
        <p>{remainTodos} {remainTodos > 1 ? 'items' : 'item'}</p>
    </div>

</section>

<style>
    ul {
        padding-left: 0px;
    }
    li {
      display: flex;
      flex-direction: row;
      align-items: center; 
      gap: 8px
    }

    li input {
        margin-bottom: 0px;
    }
</style>