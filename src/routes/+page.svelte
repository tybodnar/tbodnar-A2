<script>
     import '../style.css';
     let todoItem = '';
     let todoList = [];
     $: isDone = todoList.filter(item => item.done);

     function addToArray() {
          if (todoItem == '') {
               return;
          }
          todoList = [...todoList, {
               text: todoItem,
               done: false,

          }];
          console.log(todoList);
          todoItem = '';
     }
     function removeThis(index) {
          todoList.splice(index, 1);
          todoList = todoList;
     }
     function clearDone() {
          todoList = todoList.filter(item => !item.done)
     }
</script>

<h1>To Do List</h1>

<form on:submit|preventDefault={addToArray}  class="flex">
     <input type="text" bind:value={todoItem}>
     <div>
          <button type="submit">Add</button>
     </div>
</form>

<div class="centerList">

</div>

<!-- WORKING HERE -->

<div class="centerList">

     <ul>
          {#each todoList as item, index}
               <li>
                    <input type="checkbox" bind:checked={item.done}>

                    <span class:done={item.done} >{item.text}</span>
                    <span on:click={() => removeThis(index)} class="remove" role="button" tabindex="0">&times;</span>
               </li>
          {/each}
     </ul>

</div>

<!-- WORKING HERE -->



<div class="center">
     {#if isDone.length > 0}
     <button style="align-items: center; display: flex; justify-content: center;" on:click={clearDone}>Remove Done</button>
     {/if}
</div>




<style>
     ul {
          list-style: none;
     }
     li {
          font-size: 1.3rem;
     }
     .done {
          opacity: 25%;
          text-decoration: line-through;
     }
     .remove {
          color: darkred;
          cursor: pointer;
     }
     h1{
     text-align: center;
     padding-top: 5vw;
     }

     .flex{
          display: flex;
          justify-content: center;
          align-items: center;
          gap: 10px;
     }

     .center{
          align-items: center;
          display: flex;
          justify-content: center;
          gap: 10px;
          color: black;
     }

     .centerList{
          background-color: rebeccapurple;
          padding: 0vw 20vw;
     }

</style>