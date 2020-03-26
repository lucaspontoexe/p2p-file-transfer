<script>
  import { navigate } from "svelte-routing";

  let input;
  let file;
  let currentChunk;

  function handleFileSelect() {
    const file = input.files[0];
    window.currentFile = file;
    navigate("/send");
  }
</script>

<form>
  <label for="my-file">
    <button>choose file</button>
  </label>

  <input
    hidden
    bind:this={input}
    id="my-file"
    type="file"
    on:change={handleFileSelect} />

    <button on:click={()=>navigate('/receive')}>receive file</button>
</form>
