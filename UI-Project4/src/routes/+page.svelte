<script>
    import { fade } from 'svelte/transition';
  </script>
  
  <svelte:head>
    <title>Virtual Community Space - Home</title>
  </svelte:head>
  
  <div class="max-w-4xl mx-auto" in:fade>
    <h1 class="text-4xl font-bold mb-8 text-center">Welcome to Our Virtual Community Space</h1>
    
    <p class="text-xl mb-8 text-center">Connect with your neighbors, join interest groups, and participate in local events - all from the comfort of your home.</p>
    
    <div class="grid md:grid-cols-2 gap-8">
      <div class="bg-white p-6 rounded-lg shadow-md">
        <h2 class="text-2xl font-semibold mb-4">Virtual Spaces</h2>
        <p>Join interest-based groups and connect with like-minded individuals in your community.</p>
        <a href="/spaces" class="mt-4 inline-block bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Explore Spaces</a>
      </div>
      
      <div class="bg-white p-6 rounded-lg shadow-md">
        <h2 class="text-2xl font-semibold mb-4">Coffee Chat</h2>
        <p>Have a casual one-on-one video call with a random community member.</p>
        <a href="/coffee-chat" class="mt-4 inline-block bg-green-600 text-white px-4 py-2 rounded hover:bg-green-700">Start a Chat</a>
      </div>
      
      <div class="bg-white p-6 rounded-lg shadow-md">
        <h2 class="text-2xl font-semibold mb-4">Local Events</h2>
        <p>Discover and participate in events happening in your neighborhood.</p>
        <a href="/events" class="mt-4 inline-block bg-purple-600 text-white px-4 py-2 rounded hover:bg-purple-700">View Events</a>
      </div>
      
      <div class="bg-white p-6 rounded-lg shadow-md">
        <h2 class="text-2xl font-semibold mb-4">Safe Environment</h2>
        <p>Our platform is moderated to ensure a respectful and inclusive community for all members.</p>
      </div>
    </div>
  </div>
  
  