 <!-- two-way data binding -->
<script lang="ts">
    let list = $state(["svelte", "react", "angular", "solid", "vue", "qwik"]);
    let filteredList = $derived(list.filter((item) => item.includes(search)));
    let search = $state("");

    $inspect(search)
</script>

<!-- <input
    type="search"
    name="search"
    value={search}
    oninput={(event) => (search = event.currentTarget.value)}
/> -->

<input
    type="search"
    name="search"
    bind:value={search}
/>

<ul>
    {#each filteredList as item}
        <li>{item}</li>
    {:else}
        <p>No items found</p>
    {/each}
</ul>
