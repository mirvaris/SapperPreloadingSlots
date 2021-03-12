<script context="module">
	function waitFor(n) {
		return new Promise((y, _) => {
			setTimeout(y, n);
		})
	}
	export async function preload() {
		// await waitFor(1000);
    return {
      someData: {},
    }
	}
</script>

<script>
  import {stores} from '@sapper/app';
  import Deep1 from "../components/Deep1.svelte";
  import Deep2 from "../components/Deep2.svelte";
  import Deep3 from "../components/Deep3.svelte";
  import {tick} from "svelte";

  export let someData;

  const {preloading} = stores();

  let tickedPreloading;
  $: {
    tick().then(() => tickedPreloading = $preloading);
  }
</script>


<a href="/">Home</a>
<a href="/?a=b">Home with query param</a>

<div>
  Page: {$preloading} {tickedPreloading}
  <div {someData} />
</div>

<Deep1>
  Deep 1: {$preloading} {tickedPreloading}
  <div {someData} />
</Deep1>

<Deep2>
  Deep 2: {$preloading} {tickedPreloading}
  <div {someData} />
</Deep2>

<Deep3>
  Deep 3: {$preloading} {tickedPreloading}
  <div {someData} />
</Deep3>

<Deep3>
  Deep 3: {$preloading} {tickedPreloading}
  {JSON.stringify(someData)}
</Deep3>

<Deep3>
  Deep 3: {$preloading} {tickedPreloading} (without using props)
</Deep3>
