<script>
  import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();

  function handleInputSubmit(event) {

    console.log(event.key)

    if(event.key === 'Enter') {
      dispatch('submit', event)
    }

    return event.key;
  }

  let className;

  let defaultClass = "p-2 border-0 border-b-2 focus:border-blue-600 focus:outline-none"

  export let value;

  export let label;

  export let placeholder;

  export let labelAsPlaceholder = false;
  
  export {className as class}

</script>

{#if (label && !labelAsPlaceholder)}
   <label class="text-grey-500 text-sm">{label}</label>
{/if}
<input class={className || defaultClass} 
        placeholder={ labelAsPlaceholder ? label : placeholder } 
        type="text" 
        bind:value 
        on:keyup={handleInputSubmit} 
/>