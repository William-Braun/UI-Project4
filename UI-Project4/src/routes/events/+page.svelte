<script>
    import { fade } from 'svelte/transition';
  
    let events = [
      { id: 1, name: 'Community Garden Planting Day', date: '2023-12-15', time: '10:00 AM', icon: '🌻' },
      { id: 2, name: 'Local Author Book Signing', date: '2023-12-18', time: '2:00 PM', icon: '📚' },
      { id: 3, name: 'Neighborhood Cleanup Initiative', date: '2023-12-20', time: '9:00 AM', icon: '🧹' },
      { id: 4, name: 'Holiday Craft Fair', date: '2023-12-22', time: '11:00 AM', icon: '🎨' },
    ];
  </script>
  
  <svelte:head>
    <title>Virtual Community Space - Local Events</title>
  </svelte:head>
  
  <div in:fade>
    <h1 class="text-4xl font-bold mb-8 text-center">Local Events</h1>
    
    <p class="text-xl mb-8 text-center">Discover and participate in events happening in your community!</p>
  
    <div class="space-y-6">
      {#each events as event}
        <div class="bg-white p-6 rounded-lg shadow-md flex items-center">
          <div class="text-4xl mr-6">{event.icon}</div>
          <div class="flex-grow">
            <h2 class="text-2xl font-semibold mb-2">{event.name}</h2>
            <p class="text-gray-600">Date: {event.date}</p>
            <p class="text-gray-600">Time: {event.time}</p>
          </div>
          <button class="bg-purple-600 text-white px-4 py-2 rounded hover:bg-purple-700">RSVP</button>
        </div>
      {/each}
    </div>
  </div>
  
  