<script>
  import QRCode from "qrcode";
  import { onMount } from "svelte";

  let canvas;
  export let string = "no text yet";

  onMount(() => {
    QRCode.toCanvas(canvas, string, function(error) {
      if (error) console.error(error);
      console.log("success!");
    });
  });
</script>

<canvas id="qr-canvas" bind:this={canvas} width="256" height="256"/>