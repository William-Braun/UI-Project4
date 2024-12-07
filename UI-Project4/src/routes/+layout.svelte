<script>
    import "../app.css";
    import { page } from '$app/stores';
    import { fade } from 'svelte/transition';
</script>
  
  <div class="min-h-screen bg-gray-100 flex flex-col">
    <header class="bg-white shadow">
      <nav class="container mx-auto px-6 py-3">
        <ul class="flex space-x-4">
          <li><a href="/" class="text-gray-800 hover:text-blue-600 {$page.url.pathname === '/' ? 'font-bold' : ''}">Home</a></li>
          <li><a href="/spaces" class="text-gray-800 hover:text-blue-600 {$page.url.pathname === '/spaces' ? 'font-bold' : ''}">Spaces</a></li>
          <li><a href="/chat" class="text-gray-800 hover:text-blue-600 {$page.url.pathname === '/chat' ? 'font-bold' : ''}">Coffee Chat</a></li>
          <li><a href="/events" class="text-gray-800 hover:text-blue-600 {$page.url.pathname === '/events' ? 'font-bold' : ''}">Events</a></li>
        </ul>
      </nav>
    </header>
  
    <main class="flex-grow container mx-auto px-6 py-8" in:fade={{ duration: 250 }}>
      <slot />
    </main>
  
    <footer class="bg-gray-800 text-white py-4">
      <div class="container mx-auto px-6 text-center">
        <p>&copy; 2024 Virtual Community Space. Connecting neighbors, one click at a time.</p>
      </div>
    </footer>
  </div>
  
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');
  
    :global(body) {
      font-family: 'Inter', sans-serif;
    }
  </style>
  
  