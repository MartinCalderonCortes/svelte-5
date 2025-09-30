<script lang="ts">
    let text = $state("Any text reference");
    // derives can't be bind
    let mockingSpongeBobCase = $derived(toSpongeBobCase(text));

    // functions can't be bind
    function toSpongeBobCase(text) {
        return text
            .split("")
            .map((c: string, i: number) =>
                i % 2 === 1 ? c.toUpperCase() : c.toLowerCase(),
            )
            .join("");
    }
</script>

<!-- Doesn't work -->
<!-- <textarea bind:value={mockingSpongeBobCase}>{text}</textarea> -->

<!-- Does work -->
<!-- <textarea value={toSpongeBobCase(text)} oninput={(event) => (text = event.currentTarget.value)}></textarea> -->

<!-- Bind the value and using set and get -->
<textarea bind:value={
    () => toSpongeBobCase(text),
    (value) => {
        text = toSpongeBobCase(value)
    }
}></textarea>
