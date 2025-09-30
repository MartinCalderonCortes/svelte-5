<script lang="ts">

    let mouse = $state({ x: 0, y: 0})

    function onmousemove(event: MouseEvent) {
        mouse.x = event.clientX;
        mouse.y = event.clientY;
    }
</script>

<!-- svelte-ignore a11y_no_static_element_interactions -->
<div class="mouse" {onmousemove}>
    The mouse position is {mouse.x} x {mouse.y}
</div>