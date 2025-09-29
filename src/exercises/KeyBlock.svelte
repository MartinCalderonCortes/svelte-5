<script>
    import { fade } from "svelte/transition";

    let value = $state(0);
</script>

{#key value}
    <div in:fade class="ghost">👻</div>
{/key}

<button onclick={() => value++}>Spook</button>
