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
	import HS75Chart from './HS75Chart.svelte';
	import Footer from './Footer.svelte';
	
	let data;
	
	axios.get("https://api.npoint.io/93dee45ef70ce97af907/").then(res => {
	data = res.data;
	//console.log(data);
	});
	
</script>

<Navbar />
<TabelData data={data}/>

<div class="container">
	<MsBedahChart />
	<MsN95Chart />
	<HazmatChart />
	<GlovesSChart />
	<GlovesMChart />
	<GlovesLChart />
	<HS75Chart />
</div>

<Footer />