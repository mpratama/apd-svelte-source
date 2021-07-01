<script>
	export let data;
	let badge_rules = [
	{
		"no" : 1,
		"warning": 3,
		"ok": 5
	},
	{
		"no" : 2,
		"warning": 10,
		"ok": 30
	},
	{
		"no": 3,
		"warning": 20,
		"ok": 30
	},
	{
		"no": 4,
		"warning": 10,
		"ok": 30
	},
	{
		"no": 5,
		"warning": 1,
		"ok": 2
	},
	{
		"no": 6,
		"warning": 0,
		"ok": 0
	},
	{
		"no": 7,
		"warning": 1,
		"ok": 10
	},
	{
		"no": 8,
		"warning": 1,
		"ok": 5
	},
	{
		"no": 9,
		"warning": 1,
		"ok": 3
	},
	{
		"no": 10,
		"warning": 10,
		"ok": 30
	},
	{
		"no": 11,
		"warning": 10,
		"ok": 30
	},
	{
		"no": 12,
		"warning": 10,
		"ok": 30
	},
	{
		"no": 13,
		"warning": 1,
		"ok": 30
	},
	{
		"no": 14,
		"warning": 1,
		"ok": 30
	},
	{
		"no": 15,
		"warning": 1,
		"ok": 30
	}
];
	
</script>

<div class="container">
	
	{#if !data}
		<h4>Persediaan APD Puskesmas Kuala Sempang (Loading data, tunggu sebentar...)</h4>
		<hr style="height:3px; background-color:rgb(0,0,0);">
	{:else}
		<h4>Persediaan APD Puskesmas Kuala Sempang</h4>
		Update terakhir: {data.tanggal.tgl}
		<hr style="height:3px; background-color:rgb(0,0,0);">
	{/if}
	
	<table class="table">
		<thead>
			<tr>
				<th>No.</th>
				<th>Nama APD</th>
				<th>Satuan</th>
				<th>Jumlah</th>
			</tr>
		</thead>
		<tbody>
			{#if !data}
			<tr>
				<td>Loading...</td>
				<td>Loading...</td>
				<td>Loading...</td>
				<td>Loading...</td>
			</tr>
			<tr>
				<td>Loading...</td>
				<td>Loading...</td>
				<td>Loading...</td>
				<td>Loading...</td>
			</tr>
			<tr>
				<td>Loading...</td>
				<td>Loading...</td>
				<td>Loading...</td>
				<td>Loading...</td>
			</tr>
			<tr>
				<td>Loading...</td>
				<td>Loading...</td>
				<td>Loading...</td>
				<td>Loading...</td>
			</tr>
			<tr>
				<td>Loading...</td>
				<td>Loading...</td>
				<td>Loading...</td>
				<td>Loading...</td>
			</tr>			
			{:else}
				{#each data.barang as item, index}
				<tr>
					<td>{item.no}</td>
					<td>{item.nama}</td>
					<td>{item.sat}</td>
					
					{#if badge_rules[index].no == 5 || badge_rules[index].no == 6 || badge_rules[index].no == 10 || badge_rules[index].no == 11 || badge_rules[index].no == 12 }
						<td>{item.jml}</td>
					{:else if item.jml <= badge_rules[index].warning}
						<td>{item.jml} <span style="background:#C9182B;padding: 5px;line-height: 30px;" >Danger</span></td>
						
					{:else if item.jml > badge_rules[index].warning && item.jml <= badge_rules[index].ok}
						<td>{item.jml} <span style="background:#F08C00;padding: 5px;line-height: 30px;" >Warning</span></td>
						
					{:else}
						<td>{item.jml}</td>
					{/if}
				</tr>
				{/each}
			
			{/if}
			
		</tbody>
	</table>
	<hr style="height:3px; background-color:rgb(0,0,0);">
</div>