<script>
    import { data } from "./coordinates.svelte.js";

    const coords = $derived(data.state)
</script>

<div>
    {JSON.stringify(coords)}
</div>