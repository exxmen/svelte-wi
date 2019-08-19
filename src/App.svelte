<div class="container">
  <div class="jumbotron">

    <h1 class="display-4">Work Instructions</h1>
    <p class="lead">This is a common tool for work instructions. </p>
    <p>Please click on the button below to learn more on how to use this tool.</p>
    <a href="#" class="btn btn-primary btn-lg">Learn more</a>

  </div>

  <div class="row">
    <div class="col-sm-8">
      <input type="text" class="form-control" id="basic-url" bind:value="{url}"
        placeholder="Please enter the URL of the Work Instruction list you want to view.">
    </div>
    <div class="col-sm-4">
      {#if url!=''}
          <button class="btn btn-block btn-primary" on:click="{loadDatafromURL}">Load</button>
        {:else}
          <button class="btn btn-block btn-primary" disabled>Load</button>
        {/if}
      </div>
  </div>

  <div class="row m-2">

  </div>

  {#if loading}
    <div class="row justify-content-around">
      <div class="spinner-border" role="status">
          <span class="sr-only">Loading...</span>
      </div>
    </div>
  {:else}
    {#each data as item}
      <div class="row p-3 mb-2 bg-primary text-white">
        <div class="col-sm-1">
          <img src="{item.thumbnailUrl}" class="card-img-top" alt="...">
        </div>
        <div class="col-sm-8">
          <div class="row">
            {item.id}
          </div>
          <div class="row">
            {item.title}
          </div>
        </div>        
        <div class="col-sm-3 align-self-center">
          <a href="#" class="btn btn-secondary btn-block text-white">Open Work Instruction</a>
        </div>
      </div> 
    {/each}  
  {/if}  
</div>


<script>
  let url = '';
  let data = [];
  let loading = false;

  async function loadDatafromURL() {
    loading = true;
    const response = await fetch(url);
    const json = await response.json();
    data = json;
    console.log(data);
    loading = false;
  }
</script>