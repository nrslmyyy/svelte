<script>
	import Icon from '@iconify/svelte';
    let newItem = '';
		
    let todoList = [];

	let historyList = [];
	
	function addToList() {
		if (newItem == '') {
			pass;
		} 
		todoList = [...todoList, newItem];
		newItem = '';
		createHistory('add')
	}
	
	function removeFromList(index) {
		const tmp = todoList[index]
		todoList.splice(index, 1)
		todoList = todoList;
		createHistory('delete', tmp)
    }

	function createHistory(status, removedData) {
		const pesan = {
			add:'Add list ', 
			remove:'Delete list ' 
		}

		if (status === 'add') {

			historyList = [...historyList, pesan.add + todoList[todoList.length - 1]]
		}

		if (status === 'delete') {
			historyList = [...historyList, pesan.remove + removedData]
		}
	}

	function editList(list, index) {

	}


	
</script>

<div class="row">
	<div class="history">
		<h3>HISTORY</h3>
		<ol>
			{#each historyList as item, index}
			<li>
				{item} 
			</li>
			<br/>
			{/each}
		</ol>
	</div>
	
	<div class="wrapper">
		<h1 class="title">My Shopping List</h1>
		<div class="inputList">
			<input bind:value={newItem} type="text" placeholder="New item..">
			<button on:click={addToList}><Icon icon="material-symbols:add" /></button>
			<br/>
		</div>
		<div class="itemList">
			<ul>
				{#each todoList as item, index}
				<li>
					<span>
						{item}
					</span>
					<button on:click={() => removeFromList(index)}><Icon icon="mdi:trash-outline" /></button>
					<br>
				</li>
				{/each} 
			</ul>
			
		</div>
		
	</div>

</div>

<style> 
	* {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
	}

	.row {
		display: flex;
		justify-content: space-evenly;
		gap: 20px;
		margin: 80px 100px;
	}

	.wrapper{
		background: #fff;
		width: 100%;
		height: 400px;
		padding: 25px;
		border-radius: 5px;
		box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
	}

	.title{
		text-align: center;
		margin-bottom: 20px;
	}
	
	.inputList {
        display: flex;
        justify-content: center;
		margin-bottom: 10px;
    }
	
	.inputList input {
		background-color: white;
		width: 12em;
		height: 2em;
		padding-left: 10px;
		border-radius: 5px;
		box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
	}
	
	.inputList button {
		background-color: rgb(2, 2, 43);
		color: white;
		width: 2em;
		height: 2em;
		margin-left: 5px;
		border-radius: 5px;
		box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
	}
	
	.itemList ul {
		max-width: 250px;
		display: flex;
		justify-content: start;
		flex-direction: column;
		list-style: none;
		gap: 10px;
		margin: 0px 130px;
	}

	.itemList li {
		position: relative;
	}

	.itemList span {
		background: #f2f2f2;
		width: 4em;
		height: 8em;
		padding: 5px 5px;
		border-radius: 5px;
		border-top-right-radius: 0px;
		border-bottom-right-radius: 0px;
		box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
	}
	
	.itemList button {
		background-color: red;
		color: white;
		width: 2em;
		height: 2em;
		border-radius: 5px;
		border-top-left-radius: 0px;
		border-bottom-left-radius: 0px;
		margin-left: -5px;
		box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
	}

	.history {
		background-color: white;
		border-radius: 5px;
		padding-top: 10px;
		width: 100%;
		height: 400px;
		box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
	}

	.history h3 {
		text-align: center;
	}

	.history ol {
		color: black;
		margin: 12px 100px;
		padding-left: 10px;
	}

</style> 