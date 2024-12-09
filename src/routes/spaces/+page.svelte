<script>
    import { fade } from 'svelte/transition';
    import { Search, Users } from 'lucide-svelte'
  
    let spaces = [
      { id: 1, name: 'Gardening Enthusiasts', description: "Share tips and tricks for growing beautiful gardens.", members: 150, icon: '🌱' },
      { id: 2, name: 'Book Lovers Club', description: "Discuss your favorite books and discover new reads.", members: 200, icon: '📚' },
      { id: 3, name: 'Local History Buffs', description: "Dive into the past and share fascinating stories and facts about your community's history.", members: 75, icon: '🏛️' },
      { id: 4, name: 'Fitness and Wellness', description: "Share workout routines, wellness tips, and motivation to lead a healthier, balanced lifestyle.", members: 180, icon: '🏋️‍♀️' },
      { id: 5, name: 'Tech Talk', description: "Stay up-to-date with the latest in technology and gadgets.", members: 120, icon: '💻' },
      { id: 6, name: 'Cooking and Recipes', description: "Showcase your favorite homemade meals and share tips for creating delicious dishes.", members: 160, icon: '👨‍🍳' },
    ];

    let searchQuery = '';

    // filter spaces based on search query
    $: filteredSpaces = spaces.filter(space =>
      space.name.toLowerCase().includes(searchQuery.toLowerCase())
    );

  </script>
  
  <svelte:head>
    <title>NeighborLink - Spaces</title>
  </svelte:head>
  
  <div in:fade>
    <h1 class="text-3xl font-bold text-center pt-12 pb-8">Virtual Spaces</h1>

    <p class="text-lg mb-8 text-center">Join a space that interests you and start connecting with like-minded individuals in your community!</p>
    
    <!-- Search Bar -->
    <div class="flex gap-2 mb-8 justify-center">
      <div class="flex-1 relative max-w-7xl">
        <input
          type="text"
          placeholder="Search spaces..."
          bind:value={searchQuery}
          class="w-full px-4 py-2 rounded-md border border-gray-300 focus:outline-none focus:ring-2 focus:ring-custom-blue"
        />
        <Search class="absolute right-3 top-2.5 text-gray-400" size={20} />
      </div>
      <button class="bg-[#4C7BFF] text-white px-6 py-2 rounded-md hover:bg-blue-600 transition-colors">
        Search
      </button>
    </div>
  
    <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6 mb-12">
      {#each filteredSpaces as space}
        <div class="bg-white p-6 rounded-lg shadow-md flex flex-col">
          <!-- Icon -->
          <div class="text-4xl mb-4 text-center">{space.icon}</div>
    
          <!-- Name -->
          <h2 class="text-2xl font-semibold text-center mb-2">{space.name}</h2>
    
          <!-- Description and Button -->
          <div class="flex flex-col justify-between flex-grow">
            <!-- Description -->
            <p class="text-base text-center mb-4">{space.description}</p>
    
            <!-- Members -->
            <div class="flex items-center justify-center text-gray-600 mb-3">
              <Users size={16} class="mr-1" />
              <span class="text-sm">{space.members} members</span>
            </div>
    
            <!-- Button -->
            <button class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700 self-center">
              Join Space
            </button>
          </div>
        </div>
      {/each}
    </div>
  </div>
  
  