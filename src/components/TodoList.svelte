<div class="bg-white d-flex flex-1 todo-list m-auto h-full px-8 py-4 flex-col">
  <h1>Todo List - Svelte</h1>

  <div class="border-bottom py-2">
    <TextInput label="Infome a tarefa" on:submit={addTodo} bind:value={todo} />
    <!-- <input on:keyup={handleSubmit} class="p-2 rounded" type="text" bind:value={todo}> -->
    <button on:click={addTodo} class="p-2 rounded bg-blue-400 text-white hover:bg-blue-600">
      Adicionar Todo    
    </button>
  </div>

  {#each todos as item}
    <TodoItem on:remove={removeItem} todo={item.todo} completed={item.complete} />
  {/each}

</div>

<style>
  .todo-list {
    max-width: 800px;
  }

  h1 {
    font-size: 24px;
    font-weight: bold;
    color: #666;
  }

</style>

<script>
  
  import TodoItem from './TodoItem.svelte';
  import TextInput from './TextInput.svelte';

  export let todos;
  let todo = '';

  function addTodo() {

    console.log(todo)
    
    if (!todo) return;

    todos = [...todos, {
      todo,
      complete: false
    }]

    console.log(todos)

    todo = ''
  }

  function removeItem(event) {
    todos = todos.filter((item) => item.todo !== event.detail.todo)
  }

</script>