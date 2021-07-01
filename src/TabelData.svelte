<script>
	export let data;
	
</script>

{#if !data}
	<p>loading data...</p>
{:else}
	{#each data.barang as barang}
		<p>{barang.nama}, {barang.jml}</p>
	{/each}
{/if}