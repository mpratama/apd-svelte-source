<script>
  import axios from 'axios';
  import Chart from 'svelte-frappe-charts';
  
  let chartRef;
  
  async function getData() {
		const res = await axios.get("https://api.npoint.io/93dee45ef70ce97af907/");
		const text = await res;

		if (res.request.status == 200) {
			let datax = {
				labels: text.data.chartdata.maskerbd.x,
				datasets: [
					{
						values: text.data.chartdata.maskerbd.y
					}
				]
			};
			return datax;
		} else {
			throw new Error("Gagal menggambar grafik pengeluaran masker bedah");
		}
	}
	
	let datanya = getData();
	const onExport = () => chartRef.exportChart();

</script>


{#await datanya}
	<p>Membuat grafik pengeluaran masker bedah...</p>
{:then data}
	<Chart data={data} type="line" bind:this={chartRef} title="Pengeluaran Masker Bedah" />
	<a class="btn btn-a btn-sm smooth" on:click={onExport}>Download</a>
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}

