<script>
  import { Router, Link, Route } from "svelte-routing";

  import Button from "./components/Button.svelte";
  import QRCode from "./components/QRCode.svelte";

  import Receive from "./pages/Receive.svelte";
  import Send from "./pages/Send.svelte";

  export let url = "";
  let displayid = "hol' up, lemme import stuff";
</script>

<style>
  main {
    font-family: sans-serif;
    text-align: center;
  }
</style>

<main>
	<h1>Hello CodeSandbox</h1>
	<h2>Start editing to see some magic happen!</h2>
  test

  <Router url="{url}">
  <Route path="/send" component={Send}/>
  <Route path="/" component={Receive}/>
  </Router>

  <!-- <QRCode string={displayid}/> -->
	<Button />
</main>