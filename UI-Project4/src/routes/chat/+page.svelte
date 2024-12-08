<script>
  import { fade } from 'svelte/transition';
  
  let isMatching = false;
  let matchFound = false;
  let selectedInterests = [];  // Array to store selected interests
  let userInterests = ['Gardening', 'Books', 'Tech', 'Fitness', 'Cooking', 'History'];

  let mockMatches = [
    { name: 'John Doe', interests: ['Books', 'Tech'], profilePicture: 'https://via.placeholder.com/50' },
    { name: 'Jane Smith', interests: ['Gardening', 'Fitness'], profilePicture: 'https://via.placeholder.com/50' },
    { name: 'Alex Lee', interests: ['Cooking', 'History'], profilePicture: 'https://via.placeholder.com/50' },
  ];

  function toggleInterest(interest) {
    const index = selectedInterests.indexOf(interest);
    if (index === -1) {
      selectedInterests.push(interest); // Add the interest to the list
    } else {
      selectedInterests.splice(index, 1); // Remove the interest from the list
    }
  }

  function startMatching() {
    isMatching = true;
    setTimeout(() => {
      isMatching = false;
      matchFound = true;
    }, 3000);
  }
</script>

<svelte:head>
  <title>NeighborLink - Coffee Chat</title>
</svelte:head>

<div class="max-w-2xl mx-auto text-center" in:fade>
  <h1 class="text-3xl font-bold text-center pt-12 pb-8">Coffee Chat</h1>
  <p class="text-lg mb-8">Connect with a random community member for a casual 1-on-1 video chat!</p>

  <div class="bg-white p-8 rounded-lg shadow-md">
    {#if !isMatching && !matchFound}
      <div>
        <h2 class="text-xl mb-4">Select Your Interests</h2>
        <div class="flex flex-wrap justify-center gap-4 mb-6">
          {#each userInterests as interest}
            <button
              class="px-4 py-2 border rounded-md"
              class:bg-blue-600={selectedInterests.includes(interest)}
              class:text-white={selectedInterests.includes(interest)}
              on:click={() => toggleInterest(interest)}
            >
              {interest}
            </button>
          {/each}
        </div>
        <button
          on:click={startMatching}
          class="bg-green-600 text-white px-6 py-3 rounded-lg text-lg font-semibold hover:bg-green-700"
        >
          Start Matching
        </button>
      </div>
    {:else if isMatching}
      <p class="text-xl mb-4">Finding a match...</p>
      <div class="loader mx-auto"></div>
    {:else}
      <p class="text-xl mb-4">Match found! Click the button below to start your chat.</p>
      <button class="bg-blue-600 text-white px-6 py-3 rounded-lg text-lg font-semibold hover:bg-blue-700">
        Start Chat
      </button>
    {/if}
  </div>
</div>

<style>
  .loader {
    border: 5px solid #f3f3f3;
    border-top: 5px solid #3498db;
    border-radius: 50%;
    width: 50px;
    height: 50px;
    animation: spin 1s linear infinite;
  }

  @keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
  }
</style>
