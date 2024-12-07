<script>
    import { fade } from 'svelte/transition';
  
    let spaces = [
      { id: 1, name: 'Gardening Enthusiasts', members: 150, icon: '🌱' },
      { id: 2, name: 'Book Lovers Club', members: 200, icon: '📚' },
      { id: 3, name: 'Local History Buffs', members: 75, icon: '🏛️' },
      { id: 4, name: 'Fitness and Wellness', members: 180, icon: '🏋️‍♀️' },
      { id: 5, name: 'Tech Talk', members: 120, icon: '💻' },
      { id: 6, name: 'Cooking and Recipes', members: 160, icon: '👨‍🍳' },
    ];
  </script>
  
  <svelte:head>
    <title>Virtual Community Space - Spaces</title>
  </svelte:head>
  
  <div in:fade>
    <h1 class="text-4xl font-bold mb-8 text-center">Virtual Spaces</h1>
    
    <p class="text-xl mb-8 text-center">Join a space that interests you and start connecting with like-minded individuals in your community!</p>
  
    <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
      {#each spaces as space}
        <div class="bg-white p-6 rounded-lg shadow-md flex flex-col items-center">
          <div class="text-4xl mb-4">{space.icon}</div>
          <h2 class="text-2xl font-semibold mb-2">{space.name}</h2>
          <p class="text-gray-600 mb-4">{space.members} members</p>
          <button class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Join Space</button>
        </div>
      {/each}
    </div>
  </div>
  
  