<!-- DataFetcher.svelte -->
<script>
    import DataDisplay from "./DataDisplay.svelte";
    let data = [];
  
    async function fetchData() {
      const response = await fetch('https://api.github.com/users');
      const jsonData = await response.json();
      data = jsonData;
    }
  
    fetchData();
  </script>
  
  <!-- Display loading message or spinner while fetching data -->
  {#if data.length === 0}
    <p>Loading...</p>
  {:else}
    <!-- Once data is fetched, pass it to another component for display -->
    <DataDisplay {data} />
  {/if}