<!-- DataFetcher.svelte -->
<script>
    import DataDisplay from "./DataDisplay.svelte";
    import { onMount } from 'svelte';
    let data = [];
  
    async function fetchData() {
      const response = await fetch('https://api.github.com/users');
      const jsonData = await response.json();
      data = jsonData;
    }
  
    onMount(() => {
    fetchData(); // Fetch data immediately when the component is mounted
    const intervalId = setInterval(fetchData, 5000); // Fetch data every 60 seconds (adjust the interval as needed)

    // Cleanup function to clear the interval when the component is destroyed
    return () => {
      clearInterval(intervalId);
    };
  });

  </script>
  
  <!-- Display loading message or spinner while fetching data -->
  {#if data.length === 0}
    <p>Loading...</p>
  {:else}
    <!-- Once data is fetched, pass it to another component for display -->
    <DataDisplay {data} />
  {/if}