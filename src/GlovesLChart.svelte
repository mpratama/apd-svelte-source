<script>
  import axios from 'axios';
  import Chart from 'svelte-frappe-charts';
  
  let datachart;
	
	axios.get("https://api.npoint.io/93dee45ef70ce97af907/").then(res => {
	datachart = res.data.chartdata.glovesl;
	});

  let data = {
    labels: [],
    datasets: [
      {
        values: []
      }
    ]
  };

  let chartRef;
  
  function updateData() {
    data = {
      labels: datachart.x,
      datasets: [
        {
          values: datachart.y
        }
      ]
    };
  }
  
  setTimeout(() => {
	updateData();
  }, 5000);
  
</script>

<Chart data={data} type="line" bind:this={chartRef} title="Pengeluaran Handskun Non Steril L"/>