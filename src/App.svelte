<script>
	import axios from 'axios';
	import Navbar from './Navbar.svelte';
	import TabelData from './TabelData.svelte';
	import MsBedahChart from './MsBedahChart.svelte';
	import MsN95Chart from './MsN95Chart.svelte';
	import HazmatChart from './HazmatChart.svelte';
	import GlovesSChart from './GlovesSChart.svelte';
	import GlovesMChart from './GlovesMChart.svelte';
	import GlovesLChart from './GlovesLChart.svelte';
	
	export let data;
	
	axios.get("https://api.npoint.io/93dee45ef70ce97af907/").then(res => {
	console.log(res.data);
	data = res.data;
	});
	
</script>

<Navbar />
<TabelData data={data}/>
<MsBedahChart />
<MsN95Chart />
<HazmatChart />
<GlovesSChart />
<GlovesMChart />
<GlovesLChart />