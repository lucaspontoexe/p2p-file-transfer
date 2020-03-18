<script>
  import QRCode from "../components/QRCode";
  import Peer from "peerjs";
  import { onMount } from "svelte";

  const peer = new Peer();
  let displayid = "disconnected";

  peer.on("open", id => {
    displayid = id;
    console.log(id);
  });

  peer.on("connection", handleConnection);

  function handleConnection(conn) {
    conn.on("data", data => console.log(data));
  }
</script>

{#if displayid !== 'disconnected'}
<QRCode string={displayid}/>
{/if}