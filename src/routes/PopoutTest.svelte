<script lang="ts">
	import Popout from '$lib/Popout.svelte'
	import InheritStyleTest from './InheritStyleTest.svelte'
	import InnerStyleTest from './InnerStyleTest.svelte'
	import Sliders from './Sliders.svelte'

	let open = $state(false)
	let text = $state('write <b>some</b> html <em>here</em>!')
	let width = $state(400)
	let height = $state(400)
	let left = $state(1200)
	let top = $state(400)
</script>

<button onclick={() => (open = !open)}>{open ? 'Close' : 'Open'} Popup</button><br />
<textarea bind:value={text}></textarea> <br />
<InheritStyleTest /> <br />
<Sliders bind:width bind:left bind:height bind:top />

{#if open}
	<Popout onclose={() => (open = false)} bind:width bind:height bind:left bind:top>
		<h1>Hello micro-world!</h1>
		<InnerStyleTest />
		<InheritStyleTest />
		<p>
			{@html text}
		</p>
	</Popout>
{/if}
