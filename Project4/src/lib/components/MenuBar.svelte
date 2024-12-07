<script>
    import { goto } from '$app/navigation';
  </script>
  
  <header>
    <div class="container">
      <a href="/" class="logo">NeighborLink</a>
      <nav>
        <ul>
          <li><a href="/" on:click|preventDefault={() => goto('/')}>Home</a></li>
          <li><a href="/spaces" on:click|preventDefault={() => goto('/spaces')}>Spaces</a></li>
          <li><a href="/events" on:click|preventDefault={() => goto('/events')}>Events</a></li>
          <li><a href="/chat" on:click|preventDefault={() => goto('/chat')}>Chat</a></li>
        </ul>
      </nav>
    </div>
  </header>
  
  <style>
    header {
      background-color: #3498db;
      color: white;
      padding: 1rem 0;
    }
  
    .container {
      max-width: 1200px;
      margin: 0 auto;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 0 1rem;
    }
  
    .logo {
      font-size: 1.5rem;
      font-weight: bold;
      text-decoration: none;
      color: white;
    }
  
    nav ul {
      list-style-type: none;
      display: flex;
      gap: 1rem;
      margin: 0;
      padding: 0;
    }
  
    nav a {
      text-decoration: none;
      color: white;
      padding: 0.5rem 1rem;
      border-radius: 4px;
      transition: background-color 0.3s;
    }
  
    nav a:hover {
      background-color: rgba(255, 255, 255, 0.2);
    }
  
    @media (max-width: 768px) {
      .container {
        flex-direction: column;
        align-items: flex-start;
      }
  
      nav ul {
        margin-top: 1rem;
      }
    }
  </style>
  
  