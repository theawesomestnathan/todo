<script lang="ts">
  let newItem = "";
  let items = [
    "Wake up"
  ];

  function removeItem(index: number) {
    items = items.filter((_, i) => i !== index);
  }
</script>

<svelte:head>
  <title> Todo List </title>
</svelte:head>

<main class="flex justify-center pt-52">
  <div class="bg-slate-200 w-[30rem] p-3">
    <p class="font-bold text-4xl"> Todo </p>

    <div class="pt-3 flex space-x-2">
      <input type="text" placeholder="Wake up" bind:value={newItem} class="h-10 rounded p-2 outline-none"/>
      <button class="bg-blue-500 duration-300 hover:bg-blue-400 text-white rounded w-20" on:click={() => items = [...items, newItem]}> Add </button>
    </div>

    <div class="pt-3">
      <div class="overflow-auto bg-slate-300 p-3 h-60 space-y-2">
        {#each items as item, i}
          <div class="bg-slate-400 p-3 rounded h-12 flex justify-between">
            <p> {item} </p>

            <div>
              <button on:click={() => removeItem(i)}> ❌ </button>
            </div>
          </div>
        {/each}
      </div>
    </div>
  </div>
</main>