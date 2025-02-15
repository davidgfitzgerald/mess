<script>
    import { data } from "./coordinates.svelte.js";
    /** @type {HTMLCanvasElement | null} */
    let canvas = $state()

    /** @type {CanvasRenderingContext2D} */
    let context = $derived.by(() => {
        if (!canvas) return undefined
        return canvas.getContext("2d")
    })

    $effect(() => {
        console.log(canvas.width)
        console.log(canvas.clientWidth)
        console.log(canvas.offsetWidth)
        console.log(canvas.scrollWidth)
        for (let x = 0; x < canvas.clientWidth; x += 50) {
            context.moveTo(x, 0)
            context.strokeStyle = "black"
            context.lineWidth = 2;
            context.lineTo(x, 150)
            context.stroke()
            context.font = "48px serif";
            context.fillText("Hello world", 10, 50);
        }
        // context.fillStyle = "black"
        // context.fillRect(50, 0, 0.5, 150)
    })

    /** @type {boolean} */
    let dragging = $state(false)

    /** @param {MouseEvent} event */
    function onmousemove(event) {
        setmousecoords(event)
    }

    /** @param {MouseEvent} event */
    function onmousedown(event) {
    }

    /** @param {MouseEvent} event */
    function onmouseup(event) {
    }

    /** @param {MouseEvent} event */
    function setmousecoords(event) {
    }
</script>

<h1>Canvas</h1>

<canvas
    bind:this={canvas}
>

</canvas>

<svelte:window
    onmousemove={onmousemove}
    onmousedown={onmousedown}
    onmouseup={onmouseup}
/>

<style>
    canvas {
        border: 1px solid black;
        /* width: 100%;
        height: 100%; */
    }
</style>