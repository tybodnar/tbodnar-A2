<script>
     import '../style.css';
     let toDoItem = '';
     let toDoList = [];

     function addToArray() {
          if (toDoItem == ''){
               return;
          }
          // toDoList.push(toDoItem);
          toDoList = [...toDoList, {
               text: toDoItem,
               done: false
          }];
          console.log(toDoList);
          toDoItem = '';
     }
     function removeThis(index) {
          toDoList.splice(index, 1);
          toDoList = toDoList;
     }

</script>

<p>remember to adjust favicon!</p>

<h1>To Do!</h1>

<form on:submit|preventDefault={addToArray}>
     <input type="text" bind:value={toDoItem}>
     <button type="submit">Add</button>
</form>

<ul>
     {#each toDoList as item, index}
          <li>
               <input type="checkbox" bind:checked={item.done}>
               <span class:done={item.done} >{item.text}</span>
               <span on:click={() => removeThis(index)} class="remove" role="button" tabindex="0">&times;</span>
          </li>
     {/each}
</ul>

<style>
     ul {
          list-style: none;
     }
     li{
          font-size: 1.3rem;
     }
     .done {
          opacity: 25%;
          text-decoration: line-through;
     }
     .remove{
          color: darkred;
          cursor: pointer;
     }
</style>