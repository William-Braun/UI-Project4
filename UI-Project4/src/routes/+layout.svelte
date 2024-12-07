<script>
    import { page } from '$app/stores';
    import { fade } from 'svelte/transition';
  </script>
  
  <div class="app-container">
    <header>
      <nav>
        <ul>
          <li class:active={$page.url.pathname === '/'}>
            <a href="/">Home</a>
          </li>
          <li class:active={$page.url.pathname === '/spaces'}>
            <a href="/spaces">Virtual Spaces</a>
          </li>
          <li class:active={$page.url.pathname === '/chat'}>
            <a href="/chat">Coffee Chat</a>
          </li>
          <li class:active={$page.url.pathname === '/events'}>
            <a href="/events">Local Events</a>
          </li>
        </ul>
      </nav>
    </header>
  
    <main transition:fade={{ duration: 300 }}>
      <slot />
    </main>
  
    <footer>
      <p>&copy; 2024 Virtual Community Space. Connecting neighbors, one click at a time.</p>
    </footer>
  </div>
  
  <style>
    :global(body) {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      line-height: 1.6;
      margin: 0;
      padding: 0;
      background-color: #f0f4f8;
      color: #333;
    }
  
    .app-container {
      display: flex;
      flex-direction: column;
      min-height: 100vh;
    }
  
    header {
      background-color: #3498db;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    }
  
    nav {
      max-width: 1200px;
      margin: 0 auto;
      padding: 1rem;
    }
  
    ul {
      list-style-type: none;
      padding: 0;
      display: flex;
      justify-content: space-around;
    }
  
    li {
      display: inline;
    }
  
    a {
      color: #fff;
      text-decoration: none;
      font-weight: 500;
      padding: 0.5rem 1rem;
      border-radius: 4px;
      transition: background-color 0.3s ease;
    }
  
    a:hover {
      background-color: rgba(255,255,255,0.1);
    }
  
    .active a {
      background-color: rgba(255,255,255,0.2);
    }
  
    main {
      flex-grow: 1;
      max-width: 1200px;
      margin: 2rem auto;
      padding: 0 1rem;
    }
  
    footer {
      background-color: #34495e;
      color: #ecf0f1;
      text-align: center;
      padding: 1rem;
      margin-top: 2rem;
    }
  
    @media (max-width: 768px) {
      ul {
        flex-direction: column;
        align-items: center;
      }
  
      li {
        margin-bottom: 0.5rem;
      }
    }
  </style>
  
  