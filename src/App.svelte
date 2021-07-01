<script>
	import axios from 'axios';
	import Navbar from './Navbar.svelte';
	import TabelData from './TabelData.svelte';
	
	export let data;
	
	axios.get("https://api.npoint.io/93dee45ef70ce97af907/").then(res => {
	console.log(res.data);
	data = res.data;
	});
	
</script>

<Navbar />
<TabelData data={data}/>