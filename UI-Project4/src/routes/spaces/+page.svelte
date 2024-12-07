<script>
    import { fade, scale } from 'svelte/transition';
  
    let spaces = [
      { id: 1, name: 'Gardening Enthusiasts', members: 150, icon: '🌱' },
      { id: 2, name: 'Book Lovers Club', members: 200, icon: '📚' },
      { id: 3, name: 'Local History Buffs', members: 75, icon: '🏛️' },
      { id: 4, name: 'Fitness and Wellness', members: 180, icon: '🏋️‍♀️' },
      { id: 5, name: 'Tech Talk', members: 120, icon: '💻' },
    ];
  </script>
  
  <svelte:head>
    <title>Virtual Community Space - Spaces</title>
  </svelte:head>
  
  <div class="spaces-container" in:fade={{ duration: 300 }}>
    <h1>Virtual Spaces</h1>
  
    <p>Join a space that interests you and start connecting with like-minded individuals in your community!</p>
  
    <div class="spaces-grid">
      {#each spaces as space, index}
        <div class="space-card" in:scale={{ duration: 300, delay: index * 100 }}>
          <div class="space-icon">{space.icon}</div>
          <h2>{space.name}</h2>
          <p>{space.members} members</p>
          <button>Join Space</button>
        </div>
      {/each}
    </div>
  </div>
  
  <style>
    .spaces-container {
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
  
    .spaces-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
      gap: 1.5rem;
      margin-top: 2rem;
    }
  
    .space-card {
      background-color: #f8f9fa;
      border-radius: 8px;
      padding: 1.5rem;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
      transition: transform 0.3s ease, box-shadow 0.3s ease;
    }
  
    .space-card:hover {
      transform: translateY(-5px);
      box-shadow: 0 4px 8px rgba(0,0,0,0.15);
    }
  
    .space-icon {
      font-size: 3rem;
      margin-bottom: 1rem;
    }
  
    h2 {
      color: #3498db;
      font-size: 1.2rem;
      margin-bottom: 0.5rem;
    }
  
    button {
      background-color: #2ecc71;
      color: white;
      border: none;
      padding: 0.5rem 1rem;
      border-radius: 4px;
      cursor: pointer;
      transition: background-color 0.3s ease;
      margin-top: 1rem;
    }
  
    button:hover {
      background-color: #27ae60;
    }
  </style>
  
  