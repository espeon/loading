<script>
	import { onMount } from 'svelte';
	import { typewriter } from './transition.js';
	import { messages } from './loading-messages.js';

	let i = -1;

	onMount(() => {
		const interval = setInterval(() => {
			i = Math.round(Math.random() * messages.length - 1);
		}, 2000);

		return () => {
			clearInterval(interval);
		};
	});
</script>

<div class="lds-grid"><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div></div>
<h2>loading...</h2>

<div class="comments">
  {#key i}
    <p in:typewriter={{ speed: 10 }}>
      {messages[i] || ''}
    </p>
  {/key}
</div>