<script>
	import Header from './components/Header.svelte'
	import Footer from './components/Footer.svelte'
	import SetLIst from './components/SetList.svelte'
	import Tabs from './shared/Tabs.svelte'
	import Modal from './Modal.svelte';
	import UpdateSetForm from './components/UpdateSetForm.svelte'

	let items = ['Current Sets', 'Add New Set'];
	let activeItem = 'Current Sets';
	const tabChange = (e) => {

		activeItem = e.detail;
	}

	let sets = [];

	const handleAdd = (e) => {
		const set = e.detail;
		sets = [set, ...sets]
		activeItem = 'Current Sets'
		
	}

	let showModal = false;

	const toggleModal = () => {
		showModal = !showModal;
	}

	const tablekeys = ["select", "image", "id", "name", "year", "numParts", "price", "uvp", "best price", "status", "themeKey" , "discount", "priority"];
	let searchTerm = 42095;
	let setObject = {};

	

	let promise;
		
	async function getSets(e) {
	  try {
		// const returnValue = await fetch(`http://localhost:3000/api/v1/sets/${searchTerm}`);
		const returnValue = await fetch(`http://localhost:3000/api/v1/sets/`);
		const response = await returnValue.json();
		
		if (returnValue.ok){

			sets = response.data.sets ;
		}
		
	  } catch (error) {
		console.error(error);
	  }
	}
	// const handleGetSetClick = () => {
	// 	promise  = fetch(
	// 		`http://localhost:3000/api/v1/sets/${searchTerm}`
	// 	).then((x) => x.json());
	// }

	
	// async function searchSet(e){
	// 	try{
		
	// 	const returnValue = await fetch(`http://localhost:3000/api/v1/sets/${searchTerm}`);
	// 	const response = await returnValue.json();
		
	// 	if (returnValue.ok){
	// 		setObject =  response.data.sets
	// 	console.log(setObject)

	// 	}
		
	// 	//return response.data.sets;

	// 	}catch (error){
	// 		console.error(error);

	// 	}

	// }

		// core components
		// let promise = searchSet();
	getSets();

	//searchSet();
  </script>

<style>

main{
	max-width: 960px;
	margin: 40px auto;
}


  </style>
 
 <Header />
 <main>
	 <Tabs {activeItem} {items} on:tabChange={tabChange}/>
	{#if activeItem === 'Current Sets'}
	<SetLIst {sets} />
	{:else if activeItem === 'Add New Set'}
	<UpdateSetForm on:add={handleAdd}/>
	{/if}
	
	<Modal {showModal} on:click={toggleModal}>
		<UpdateSetForm />
	</Modal>
	 <button on:click={toggleModal}>Open Edit</button>

		<!-- <label for="searchterm">Please enter a set Id</label>
		<input type=text id="searchterm" bind:value={searchTerm}>
	<button on:click={searchSet}>Search</button> -->
	
	<!-- <button on:click={handleGetSetClick}>Get Set</button> -->
	<!-- {#await promise}
	<p>...waiting</p>
	{:then data}
	<p>{JSON.stringify(data, null, 2)}</p>
	{/await}
		{#if sets.length > 0} -->
		<!-- <table>
		
		<thead>
			<tr>
				{#each tablekeys as key}
				<td>{key}</td>
				{/each}
			</tr>
		</thead>
		<tbody>
			{#each sets as set}
				<tr id=set.setID > 
					<td><input type="checkbox"></td>
					<td><img src={set.imageUrl} media="(max-width: 100px)" alt="set image"></td>
					<td>{set.setId}</td>
					<td>{set.name}</td>
					<td>{set.year}</td>
					<td>{set.numParts}</td>
					<td>{set.price}</td>
					<td>{set.priceUvp}</td>
					<td>{set.priceBest}</td>
					<td>{set.status}</td>
					<td>{set.themeKey}</td>
					<td>{set.discount}</td>
					<td>{set.priority}</td>
					
				</tr>
			{/each}
			
		</tbody>
		
	</table>
	{:else}No sets to show yet{/if} -->


 </main>
 <Footer />

	
