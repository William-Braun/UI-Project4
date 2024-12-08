<script>
  import { Users, Coffee, Calendar, MessageSquare } from 'lucide-svelte';
  import { fade } from 'svelte/transition';

  const upcomingEvents = [
    {
      title: 'Virtual Book Club',
      date: 'Dec 10, 2023',
      attendees: 15
    },
    {
      title: 'Local Gardening Workshop',
      date: 'Dec 12, 2023',
      attendees: 8
    },
    {
      title: 'Community Game Night',
      date: 'Dec 15, 2023',
      attendees: 20
    }
  ];
</script>

<svelte:head>
  <title>NeighborLink - Home</title>
</svelte:head>

<div class="min-h-screen flex flex-col" in:fade>
  <!-- Hero Section -->
  <div class="flex justify-center">
    <div class="bg-[#DDEAFD] w-[70%] py-16 px-4 text-center">
      <h1 class="text-4xl font-bold mb-4">Welcome to Your Digital Neighborhood</h1>
      <p class="text-lg text-gray-900 mb-8">Connect, share, and grow with your local community and beyond.</p>
      <button class="bg-[#4C7BFF] text-white text-lg font-semibold px-6 py-2 rounded hover:bg-blue-600 transition-colors">
        Join NeighborLink
      </button>
    </div>
  </div>

  <!-- Features Section -->
  <div class="max-w-7xl mx-auto px-4 py-16 w-full">
    <h2 class="text-2xl font-bold text-center mb-12">Discover Our Features</h2>
    
    <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
      <div class="bg-white p-6 rounded shadow">
        <div class="text-[#4C7BFF] mb-4">
          <Users size={24} />
        </div>
        <h3 class="font-semibold text-lg mb-2">Virtual Spaces</h3>
        <p class="text-gray-600 text-sm">Join topic-based rooms and connect with like-minded individuals.</p>
      </div>

      <div class="bg-white p-6 rounded shadow">
        <div class="text-[#4C7BFF] mb-4">
          <Coffee size={24} />
        </div>
        <h3 class="font-semibold text-lg mb-2">Coffee Chats</h3>
        <p class="text-gray-600 text-sm">Have spontaneous 1-on-1 video calls with community members.</p>
      </div>

      <div class="bg-white p-6 rounded shadow">
        <div class="text-[#4C7BFF] mb-4">
          <Calendar size={24} />
        </div>
        <h3 class="font-semibold text-lg mb-2">Local Events</h3>
        <p class="text-gray-600 text-sm">Discover and join events happening in your area.</p>
      </div>

      <div class="bg-white p-6 rounded shadow">
        <div class="text-[#4C7BFF] mb-4">
          <MessageSquare size={24} />
        </div>
        <h3 class="font-semibold text-lg mb-2">Community Forums</h3>
        <p class="text-gray-600 text-sm">Engage in ongoing, structured discussions on various topics.</p>
      </div>
    </div>
  </div>

  <!-- Upcoming Events Section -->
  <div class="max-w-7xl mx-auto px-4 pb-16 w-full">
    <h2 class="text-2xl font-bold text-center mb-12">Upcoming Events</h2>
    
    <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
      {#each upcomingEvents as event}
        <div class="bg-white p-6 rounded shadow">
          <h3 class="font-semibold text-lg mb-2">{event.title}</h3>
          <p class="text-gray-600 text-sm mb-2">{event.date}</p>
          <p class="text-gray-600 text-sm mb-4">{event.attendees} attendees</p>
          <button class="bg-[#4C7BFF] text-white px-4 py-1 rounded text-sm hover:bg-blue-600 transition-colors">
            RSVP
          </button>
        </div>
      {/each}
    </div>
  </div>
</div>

<style>
  :global(body) {
    background-color: #f8fafc;
  }
</style>

