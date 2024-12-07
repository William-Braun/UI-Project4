<script>
    import { fade, fly } from 'svelte/transition';
  
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
  
  <div class="coffee-chat-container" in:fade={{ duration: 300 }}>
    <h1>Coffee Chat</h1>
  
    <p>Connect with a random community member for a casual 1-on-1 video chat.</p>
  
    <div class="chat-area">
      {#if !isMatching && !matchFound}
        <button on:click={startMatching} in:fly={{ y: 20, duration: 300 }}>Start Matching</button>
      {:else if isMatching}
        <p in:fade>Finding a match...</p>
        <div class="loader" in:fade></div>
      {:else}
        <p in:fade>Match found! Click the button below to start your chat.</p>
        <button in:fly={{ y: 20, duration: 300 }}>Start Chat</button>
      {/if}
    </div>
  </div>
  
  <style>
    .coffee-chat-container {
      background-color: #ffffff;
      border-radius: 8px;
      padding: 2rem;
      box-shadow: 0 4px 6px rgba(0,0,0,0.1);
      text-align: center;
    }
  
    h1 {
      color: #2c3e50;
      font-size: 2.5rem;
      margin-bottom: 1rem;
    }
  
    .chat-area {
      margin-top: 2rem;
      display: flex;
      flex-direction: column;
      align-items: center;
    }
  
    button {
      background-color: #e67e22;
      color: white;
      border: none;
      padding: 0.75rem 1.5rem;
      border-radius: 4px;
      cursor: pointer;
      transition: background-color 0.3s ease;
      font-size: 1.1rem;
    }
  
    button:hover {
      background-color: #d35400;
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
  
  