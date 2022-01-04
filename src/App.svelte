<script>

	import Footer from "./components/Footer.svelte";
	import Header from "./components/Header.svelte";
	import PollList from "./components/PollList.svelte";
	import CreatePollForm from "./components/CreatePollForm.svelte";
	import Tabs from "./shared/Tabs.svelte";
	import "smelte/src/tailwind.css"
	
	
	let items = ['Current Polls', 'Add New Poll'];
	let activeItem = 'Current Polls';

	const tabchange = (e) => {
		activeItem = e.detail;
	}


	// polls
	// let polls = [
	// 	{
	// 		id: 1,
	// 		question: 'Python or JavaScript',
	// 		answerA: 'Python',
	// 		answerB: 'JavaScript',
	// 		votesA: 9,
	// 		votesB: 15
	// 	}
	// ]

	const handleAdd = (e) => {
		// const poll = e.detail
		// polls = [poll, ...polls]
		activeItem = 'Current Polls'
		console.log(polls)
	}

	import {
	  Button,
	  Menu,
	} from "smelte";
  
	let open = true;
	  let selected = "";
  
	const itemss = [
		  { value: 1, text: 'One' },
		  { value: 2, text: 'Two' },
		  { value: 3, text: 'Three' },
		  { value: 4, text: 'Four' },
		  { value: 5, text: 'Five' },
	  ];
	

</script>

<Header/>
<main>
	<Tabs {activeItem} {items} on:tabChange={tabchange}/>

	{#if activeItem === 'Current Polls'}
		<PollList />
	{:else if activeItem === 'Add New Poll'}
		<CreatePollForm on:add={handleAdd}/>	
	{/if}

	<small>Selected: {selected || 'nothing'}</small>
  
  <Menu bind:open {itemss} bind:value={selected}>
	  <div slot="activator">
		  <Button on:click={() => open = !open}>A menu</Button>
	  </div>
  </Menu>
</main>
<Footer/>
<style>
	main{
		max-width: 960px;
		margin: 40px auto;
	}
</style>


  