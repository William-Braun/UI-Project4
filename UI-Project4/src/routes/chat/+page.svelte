<script>
    import { fade } from 'svelte/transition';
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
  
  <div class="max-w-2xl mx-auto text-center" in:fade>
    <h1 class="text-4xl font-bold mb-8">Coffee Chat</h1>
    
    <p class="text-xl mb-8">Connect with a random community member for a casual 1-on-1 video chat.</p>
  
    <div class="bg-white p-8 rounded-lg shadow-md">
      {#if !isMatching && !matchFound}
        <button on:click={startMatching} class="bg-green-600 text-white px-6 py-3 rounded-lg text-lg font-semibold hover:bg-green-700">
          Start Matching
        </button>
      {:else if isMatching}
        <p class="text-xl mb-4">Finding a match...</p>
        <div class="loader mx-auto"></div>
      {:else}
        <p class="text-xl mb-4">Match found! Click the button below to start your chat.</p>
        <button class="bg-blue-600 text-white px-6 py-3 rounded-lg text-lg font-semibold hover:bg-blue-700">
          Start Chat
        </button>
      {/if}
    </div>
  </div>
  
  <style>
    .loader {
      border: 5px solid #f3f3f3;
      border-top: 5px solid #3498db;
      border-radius: 50%;
      width: 50px;
      height: 50px;
      animation: spin 1s linear infinite;
    }
  
    @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }
  </style>
  
  