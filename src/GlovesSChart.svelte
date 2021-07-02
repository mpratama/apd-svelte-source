<script>
  import axios from 'axios';
  import Chart from 'svelte-frappe-charts';
  
  let chartRef;
  
  async function getData() {
		const res = await axios.get("https://api.npoint.io/93dee45ef70ce97af907/");
		const text = await res;

		if (res.request.status == 200) {
			let datax = {
				labels: text.data.chartdata.glovess.x,
				datasets: [
					{
						values: text.data.chartdata.glovess.y
					}
				]
			};
			return datax;
		} else {
			throw new Error("Gagal menggambar grafik pengeluaran handskun no steril S");
		}
	}
	
	let datanya = getData();

</script>


{#await datanya}
	<p>Membuat grafik pengeluaran handskun non steril size S...</p>
{:then data}
	<Chart data={data} type="line" bind:this={chartRef} title="Pengeluaran Handskun Non Steril Size S" />
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}