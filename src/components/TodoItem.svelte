<script>
  import { createEventDispatcher } from 'svelte';

  export let todo
  export let completed

  const dispatch = createEventDispatcher();

</script>

<div class="todo-item">
  <input type="checkbox" bind:checked={completed}>
  <span class:complete={completed}>{todo}</span>
  <div class="todo-actions">
    <button class="btn-danger" on:click={dispatch('remove', { todo })}>Excluir</button>
  </div>
</div>

<style>
  .todo-actions {
    display: flex;
    right: 0;
    margin-right: 0;
    margin-left: auto;
    padding-right: 8px;
  }

  .todo-item {
    display: flex;
    align-items: center;
    width: 100%;
    padding: 8px 0;
    border-bottom: 1px solid #404040;  
  }

  .todo-item:hover {
    background-color: #c5c5c6
  }

  input[type=checkbox] {
    margin-right: 8px;
    margin-left: 8px;
  }

  .complete {
    text-decoration: line-through;
  }

  .btn-danger {
    @apply p-2 rounded bg-red-600 text-white;
  }

  .btn-danger:hover {
    @apply bg-red-800;
  }
</style>