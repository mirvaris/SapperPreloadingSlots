<script context="module">
	export async function preload() {
    return {
      exportedProp: {},
    }
	}
</script>

<script>
  import {stores} from '@sapper/app';
  import Deep1 from "../components/Deep1.svelte";
  import Deep2 from "../components/Deep2.svelte";
  import Deep3 from "../components/Deep3.svelte";
  import {tick} from "svelte";

  export let exportedProp;

  const myVariable = {};

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
  <div {exportedProp} />
</div>

<Deep1>
  Deep 1: {$preloading} {tickedPreloading}
  <div {exportedProp} />
</Deep1>

<Deep2>
  Deep 2: {$preloading} {tickedPreloading}
  <div {exportedProp} />
</Deep2>

<Deep3>
  Deep 3: {$preloading} {tickedPreloading}
  <div {exportedProp} />
</Deep3>

<Deep3>
  Deep 3: {$preloading} {tickedPreloading}
  {JSON.stringify(exportedProp)}
</Deep3>

<Deep3>
  Deep 3: {$preloading} {tickedPreloading} (without using props)
  {myVariable}
</Deep3>
