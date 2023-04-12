<script>
    let newItem = '';

    let todoList = [{text: 'Explore svelte', status: false},
                    {text: 'Do coding stuff', status: false},
                    {text: 'Eat snacks', status: true},
					{text: 'sleep well', status: false}];
	
	function addToList() {
        if (newItem!==''){
            todoList = [...todoList, {text: newItem, status: false}];
        }
		else{
				invalid()
		}
		
		newItem = '';
	}
	function invalid(){
		alert('Please Add Some Item')
	}
	// @ts-ignore
	function removeFromList(index) {
		todoList.splice(index, 1)
		todoList = todoList;
    }
</script>
<div class="mainContainer">
	<h1>Welcome, Ashok</h1>
	<h3>You've got {todoList.length} Upcoming Tasks</h3>
	<input bind:value={newItem} type="text" placeholder="Add ToDo Items" style="padding: 10px 30px;margin:40px 0" on:invalid={invalid}>
	
	<button on:click={addToList} style="padding: 10px 30px">Add</button>
	<br/>
	<div style="margin: 5px 0;">
		{#each todoList as item, index}
		<div class="item">
		<input bind:checked={item.status} type="checkbox">
		<span class:checked={item.status}>{item.text}</span>
		<button on:click={() => removeFromList(index)} >X </button>
		</div>
		<br/>
		{/each} 
	</div>
</div>




<style> 
	.checked {
        text-decoration:line-through;
    }
	.mainContainer{
		margin: 100px;
	}
	.item{
		background-color: #efefef;
		border-radius: 5px;
		width: max-content;
		padding: 15px;
		display: flex;
		justify-content: space-between;
		width: 30%;
	}
</style> 