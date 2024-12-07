<script>
  let isMatching = false;
  let matchFound = false;

  function startMatching() {
    isMatching = true;
    setTimeout(() => {
      isMatching = false;
      matchFound = true;
    }, 3000);
  }
</script>

<svelte:head>
  <title>Virtual Community Space - Coffee Chat</title>
</svelte:head>

<h1>Coffee Chat</h1>

<p>Connect with a random community member for a casual 1-on-1 video chat.</p>

{#if !isMatching && !matchFound}
  <button on:click={startMatching}>Start Matching</button>
{:else if isMatching}
  <p>Finding a match...</p>
  <div class="loader"></div>
{:else}
  <p>Match found! Click the button below to start your chat.</p>
  <button>Start Chat</button>
{/if}

<style>
  button {
    background-color: #008CBA;
    color: white;
    border: none;
    padding: 0.5rem 1rem;
    border-radius: 4px;
    cursor: pointer;
  }

  button:hover {
    background-color: #007B9A;
  }

  .loader {
    border: 5px solid #f3f3f3;
    border-top: 5px solid #3498db;
    border-radius: 50%;
    width: 50px;
    height: 50px;
    animation: spin 1s linear infinite;
    margin: 20px auto;
  }

  @keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
  }
</style>

