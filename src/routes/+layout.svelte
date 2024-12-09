<script>
  import { page } from '$app/stores';
  import '../app.css';

  export const prerender = true;
</script>

<div class="min-h-screen flex flex-col">
  <header class="bg-[#4C7BFF] text-white">
    <nav class="max-w-7xl mx-auto px-6 py-4">
      <ul class="flex space-x-6 justify-center">
        <li><a href="/" class="hover:text-blue-100 hover:underline text-lg {$page.url.pathname === '/' ? 'font-bold' : ''}">Home</a></li>
        <li><a href="/spaces" class="hover:text-blue-100 hover:underline text-lg {$page.url.pathname === '/spaces' ? 'font-bold' : ''}">Spaces</a></li>
        <li><a href="/events" class="hover:text-blue-100 hover:underline text-lg {$page.url.pathname === '/events' ? 'font-bold' : ''}">Events</a></li>
        <li><a href="/chat" class="hover:text-blue-100 hover:underline text-lg {$page.url.pathname === '/chat' ? 'font-bold' : ''}">Chat</a></li>
      </ul>
    </nav>
  </header>

  <slot />

  <!-- Footer -->
  <div class="mt-auto bg-[#4C7BFF] text-white py-6">
    <div class="max-w-7xl mx-auto px-4 flex flex-col md:flex-row justify-between items-center">
      <div>
        <h3 class="font-semibold text-2xl mb-2">NeighborLink</h3>
        <p class="text-base text-blue-100">Connecting communities, one click at a time.</p>
      </div>
      <div class="mt-4 md:mt-0">
        <h4 class="text-lg font-semibold mb-2">Stay Connected</h4>
        <div class="flex gap-2">
          <input
            type="email"
            placeholder="Enter your email"
            class="px-3 py-1 rounded text-gray-800 text-base"
          />
          <button class="bg-white text-[#4C7BFF] px-4 py-1 rounded text-base hover:bg-blue-100 transition-colors">
            Subscribe
          </button>
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

  :global(body) {
    font-family: 'Inter', sans-serif;
    margin: 0;
    padding: 0;
  }
</style>

