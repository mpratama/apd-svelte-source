<script>
  import axios from 'axios';
  import Chart from 'svelte-frappe-charts';
  
  let chartRef;
  
  
  async function getData() {
		const res = await axios.get("https://api.npoint.io/93dee45ef70ce97af907/");
		const text = await res;

		if (res.request.status == 200) {
			let datax = {
				labels: text.data.chartdata.hs75.x,
				datasets: [
					{
						values: text.data.chartdata.hs75.y
					}
				]
			};
			return datax;
		} else {
			throw new Error("Gagal menggambar grafik pengeluaran handskun steril 7.5");
		}
	}
	
	let datanya = getData();
	const onExport = () => chartRef.exportChart();

</script>


{#await datanya}
	<p>Membuat grafik pengeluaran handskun steril 7.5</p>
{:then data}
	<Chart data={data} type="line" bind:this={chartRef} title="Pengeluaran Handskun Steril 7-5" />
	<a class="btn btn-a btn-sm smooth" on:click={onExport}>Download</a>
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}