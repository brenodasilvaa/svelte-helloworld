<!-- DataDisplay.svelte -->
<script>
    export let data;
  </script>
  <div class="div1">
    {#each data as item}
    <div class="div2">
        <input style="width: 50rem;" disabled type="text" value={item.login}>
        <input disabled type="text" value={item.avatar_url}>
        <br>
    </div>
    {/each}
  </div>

  <style>
    .div1{
        display: flex;
        flex-direction: column;;
        justify-content: center;
        align-items: center;
    }

    .div2{
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
    }
  </style>