<script>
    import { fade } from 'svelte/transition';
    import { Search } from 'lucide-svelte'

    let events = [
      { id: 1, name: 'Community Garden Planting Day', date: 'Dec 15, 2024', time: '10:00 AM', icon: '🌻', attendees: 25 },
      { id: 2, name: 'Local Author Book Signing', date: 'Dec 18, 2024', time: '2:00 PM', icon: '📚', attendees: 40 },
      { id: 3, name: 'Neighborhood Cleanup Initiative', date: 'Dec 21, 2024', time: '9:00 AM', icon: '🧹', attendees: 15 },
      { id: 4, name: 'Holiday Craft Fair', date: 'Dec 22, 2024', time: '11:00 AM', icon: '🎨', attendees: 50 },
    ];

    let searchQuery = '';

    // filter events based on search query
    $: filteredEvents = events.filter(event =>
      event.name.toLowerCase().includes(searchQuery.toLowerCase())
    );

  </script>
  
  <svelte:head>
    <title>NeighborLink - Local Events</title>
  </svelte:head>
  
  <div in:fade>
    <h1 class="text-3xl font-bold text-center pt-12 pb-8">Local Events</h1>

    <p class="text-lg mb-8 text-center">Discover and participate in events happening in your community!</p>
    
    <!-- Search Bar -->
    <div class="flex gap-2 mb-8 justify-center">
      <div class="flex-1 relative max-w-7xl">
        <input
          type="text"
          placeholder="Search events..."
          bind:value={searchQuery}
          class="w-full px-4 py-2 rounded-md border border-gray-300 focus:outline-none focus:ring-2 focus:ring-custom-blue"
        />
        <Search class="absolute right-3 top-2.5 text-gray-400" size={20} />
      </div>
      <button class="bg-[#4C7BFF] text-white px-6 py-2 rounded-md hover:bg-blue-600 transition-colors">
        Search
      </button>
    </div>
  
    <div class="space-y-6 mb-12">
      {#each filteredEvents as event}
        <div class="bg-white p-6 rounded-lg shadow-md flex items-center">
          <div class="text-4xl mr-6">{event.icon}</div>
          <div class="flex-grow">
            <h2 class="text-2xl font-semibold mb-2">{event.name}</h2>
            <p class="text-gray-600">Date: {event.date}</p>
            <p class="text-gray-600">Time: {event.time}</p>
            <p class="text-gray-600">{event.attendees} attendees</p>
          </div>
          <button class="bg-purple-600 text-white px-4 py-2 rounded hover:bg-purple-700">RSVP</button>
        </div>
      {/each}
    </div>
  </div>
  
  