<script>
    let newItem = '';
		
    let todoList = [];
	
	function addToList() {
		todoList = [...todoList, {text: newItem, status: false}];
		newItem = '';
	}
	
	function removeFromList(index) {
		todoList.splice(index, 1)
		todoList = todoList;
    }
</script>

<div class="inputList">
    <input bind:value={newItem} type="text" placeholder="new todo item..">
    <button on:click={addToList}>Add</button>

    <br/>
<ul>
	{#each todoList as item, index}
	<li>
	<span >{item.text}</span>
	<button on:click={() => removeFromList(index)}>Delete</button>
	<br/>
	</li>
    {/each} 
</ul>
</div>

<style> 
	.inputList {
        display: flex;
        justify-content: center;
    }
</style> 