<script>
  import axios from 'axios';
  import Chart from 'svelte-frappe-charts';
  
  let chartRef;
  
  async function getData() {
		const res = await axios.get("https://api.npoint.io/93dee45ef70ce97af907/");
		const text = await res;

		if (res.request.status == 200) {
			let datax = {
				labels: text.data.chartdata.maskern95.x,
				datasets: [
					{
						values: text.data.chartdata.maskern95.y
					}
				]
			};
			return datax;
		} else {
			throw new Error("Gagal menggambar grafik pengeluaran masker N95");
		}
	}
	
	let datanya = getData();

</script>


{#await datanya}
	<p>Membuat grafik pengeluaran N95 ...</p>
{:then data}
	<Chart data={data} type="line" bind:this={chartRef} title="Pengeluaran Masker N95" />
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}

