<script>
  import logo from './assets/svelte.png'
  import Counter from './lib/Counter.svelte'
  import ComponentBuild from './lib/ComponentBuild.svelte'

  let components = [{
    name: "CPU AMD Ryzen 4700G",
    price: 300
  },
  {
      name: "NVIDIA 1660 Super",
      price: 400
  }]

  let filter=""
  let nameNewComponent=""
  let priceNewComponent=""
  $: filteredComponents = components.filter(el => el.name.includes(filter))

  const addNewComponent = () =>{
    components.push({
      name: nameNewComponent,
      price: priceNewComponent
    })
    components = components
  }
  
</script>

<main class="text-white text-center p-1 m-0">
  <h1 class="text-orange-600 uppercase font text-7xl font-thin leading-tight m-8 max-w-xs">PC Component list</h1>

  <div class="flex flex-col items-center">
    
    <h3 class="font-bold text-lg">Nuovo componente</h3>
    
    Nome: <input class="rounded bg-zinc-600 w-60" type="text" bind:value={nameNewComponent}/>
    Prezzo: <input class="rounded bg-zinc-600 w-60" type="number" bind:value={priceNewComponent}/>
    
    <button class="rounded bg-orange-700 text-white w-20 m-2" on:click={addNewComponent}>Add</button>
    
  </div><br><br>
  
  Filtro: <input class="rounded bg-zinc-600" type="text" bind:value={filter}/>

  {#each filteredComponents as component}
      <ComponentBuild {component}/>
  {/each}

</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  p {
    max-width: 14rem;
    margin: 1rem auto;
    line-height: 1.35;
  }

  @media (min-width: 480px) {
    h1 {
      max-width: none;
    }

    p {
      max-width: none;
    }
  }
</style>
