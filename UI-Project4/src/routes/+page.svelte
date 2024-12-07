<script>
    import { onMount } from 'svelte';
    import { fade, fly } from 'svelte/transition';
    
    let greeting = '';
    
    onMount(() => {
      const hours = new Date().getHours();
      if (hours < 12) greeting = 'Good morning';
      else if (hours < 18) greeting = 'Good afternoon';
      else greeting = 'Good evening';
    });
  </script>
  
  <svelte:head>
    <title>Virtual Community Space - Home</title>
  </svelte:head>
  
  <div class="home-container">
    <h1 in:fade={{ duration: 300, delay: 300 }}>{greeting}, neighbor!</h1>
  
    <p in:fade={{ duration: 300, delay: 600 }}>Welcome to our Virtual Community Space, where distance is no barrier to meaningful connections.</p>
  
    <div class="features" in:fade={{ duration: 300, delay: 900 }}>
      <h2>What we offer:</h2>
      <ul>
        <li in:fly={{ y: 20, duration: 300, delay: 1200 }}>
          <span class="icon">🌐</span>
          <span>Virtual interest-based spaces</span>
        </li>
        <li in:fly={{ y: 20, duration: 300, delay: 1400 }}>
          <span class="icon">☕</span>
          <span>Random coffee chats</span>
        </li>
        <li in:fly={{ y: 20, duration: 300, delay: 1600 }}>
          <span class="icon">📅</span>
          <span>Local event discovery</span>
        </li>
        <li in:fly={{ y: 20, duration: 300, delay: 1800 }}>
          <span class="icon">🛡️</span>
          <span>A safe, moderated environment for genuine interactions</span>
        </li>
      </ul>
    </div>
  
    <p class="cta" in:fade={{ duration: 300, delay: 2100 }}>Start exploring and connect with your community today!</p>
  </div>
  
  <style>
    .home-container {
      background-color: #ffffff;
      border-radius: 8px;
      padding: 2rem;
      box-shadow: 0 4px 6px rgba(0,0,0,0.1);
    }
  
    h1 {
      color: #2c3e50;
      font-size: 2.5rem;
      margin-bottom: 1rem;
    }
  
    .features {
      margin-top: 2rem;
    }
  
    h2 {
      color: #3498db;
      font-size: 1.5rem;
      margin-bottom: 1rem;
    }
  
    ul {
      list-style-type: none;
      padding: 0;
    }
  
    li {
      display: flex;
      align-items: center;
      margin-bottom: 1rem;
    }
  
    .icon {
      font-size: 1.5rem;
      margin-right: 1rem;
      width: 2rem;
      text-align: center;
    }
  
    .cta {
      margin-top: 2rem;
      font-weight: bold;
      color: #e74c3c;
    }
  </style>
  
  