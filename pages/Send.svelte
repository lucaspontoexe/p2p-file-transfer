<script>
  import Peer from "peerjs";
  import Instascan from "@mathewparet/instascan";
  import { onMount } from "svelte";

  let video;
  let fileSelector;
  let result;

  const peer = new Peer();

  var fileReader = new FileReader();
  const whatIf = new Uint8Array([0, 2, 4, 8]);

  onMount(async () => {
    const scanner = new Instascan.Scanner({ video, mirror: false });
    const cameras = await Instascan.Camera.getCameras();
    if (cameras.length > 0) scanner.start(cameras[1]);
    scanner.addListener("scan", onScan);
  });

  function onScan(data) {
    console.log(data);
    result = data;
    handleConnection(data);
  }

  function handleConnection(id) {
    const conn = peer.connect(id);
    conn.on("open", () => {
      conn.send("hi! mas olha só");
      conn.send(whatIf);
    });
  }
</script>


<div class="send-page">
	send
  <video bind:this={video} class="camera" />
  <input bind:this={fileSelector} id="my-file" type="file" />
  <p>result: {result}</p>
</div>

<style>
  video {
    z-index: -1;
    width: 100vw;
    height: 100vh;
    object-fit: cover;
    height: auto;
    position: absolute;
    top: 0px;
    left: 0px;
  }
  .send-page {
    z-index: 1;
  }
</style>