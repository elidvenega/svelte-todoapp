<script>
  let newItem = "";

  let todoList = [
    { task: "Go Hiking", status: false },
    { task: "Groceries", status: false },
    { task: "Washing", status: false },
    { task: "Study", status: false }
  ];

  function addTodo() {
    todoList = [...todoList, { task: newItem, status: false }];
    newItem = "";
  }

  function deleteTodo(index) {
    todoList.splice(index, 1);
    todoList = todoList;
  }
</script>

<h1>Svelte Todo List</h1>
<div class="todo-list-container">
  <input
    bind:value={newItem}
    class="input"
    placeholder="Add todo"
    type="text"
    name="todo-list"
  />
  <button class="add-todo-button" on:click={addTodo}>Add Todo</button>
  <br />
  {#each todoList as item, index}
    <div>
      <input bind:checked={item.status} type="checkbox" />
      <span class:checked={item.status}>{item.task}</span>
      <!-- svelte-ignore a11y-click-events-have-key-events -->
      <!-- svelte-ignore a11y-no-static-element-interactions -->
      <span class="delete-button" on:click={() => deleteTodo(index)}>❌</span>
    </div>
  {/each}
</div>

<style>
  :root {
    --color-one: #f97316;
    --white-color: #fff;
    --font-size: 1rem;
  }

  h1 {
    color: var(--color-one);
    text-align: center;
    font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
      "Lucida Sans", Arial, sans-serif;
    font-size: calc(var(--font-size) * 3);
  }

  .todo-list-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin: 0 auto;
    margin-top: 2rem;
    gap: 5px;
    width: 30rem;
  }

  input {
    padding: 10px;
  }

  .checked {
    text-decoration: line-through;
  }

  .delete-button {
    cursor: pointer;
  }

  .add-todo-button {
    background-color: var(--color-one);
    border: none;
    color: var(--white-color);
    padding: 10px;
  }
  
  span {
    font-size: 1.2rem;
  }
  /* .add-todo-button {
    width: 4rem;
  } */
</style>
