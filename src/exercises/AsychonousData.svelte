<script lang="ts">
    async function getPokemon(pokemon: string) {
        const baseUrl = "https://pokeapi.co/api/v2/pokemon";
        const response = await fetch(`${baseUrl}/${pokemon}`);
        if (!response.ok) throw new Error("💣️ oops!");
        let { name, sprites } = await response.json();
        return { name, image: sprites["front_default"] };
    }
</script>

{#await getPokemon("snorlax")}
    <p>Loading...</p>
{:then pokemon}
    <div class="pokemon-details">
        <p>{pokemon.name}</p>
        <img src={pokemon.image} alt={pokemon.name} />
    </div>
{:catch error}
    <p>{error.message}</p>
{/await}

<!-- {#await getPokemon("pikachu") then pokemon}
    <div class="pokemon-details">
        <p>{pokemon.name}</p>
        <img src={pokemon.image} alt={pokemon.name} />
    </div>
{/await} -->
