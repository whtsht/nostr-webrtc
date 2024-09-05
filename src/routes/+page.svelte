<script lang="ts">
	import { SimplePool, type Filter } from 'nostr-tools';

	const RELAYS = [
		'wss://nostr.mutinywallet.com',
		'wss://relay.snort.social',
		'wss://nostr.wine',
		'wss://nos.lol',
		'wss://relay.damus.io'
	];

	async function main() {
		const pool = new SimplePool();
		const filters: Filter[] = [{ kinds: [1], limit: 100 }];
		pool.subscribeMany(RELAYS, filters, {
			onevent(event) {
				console.log(event);
			}
		});
		console.log(pool);
		return pool;
	}
</script>

<h1>Nostr Storage</h1>

{#await main()}
	waiting...
{:then value}
	{value}
{:catch error}
	{error}
{/await}
