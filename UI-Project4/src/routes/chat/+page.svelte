<script>
  import { fade } from 'svelte/transition';

  let isMatching = false;
  let matchFound = false;
  let selectedInterests = [];  // Array to store selected interests
  let userInterests = ['Gardening', 'Books', 'Tech', 'Fitness', 'Cooking', 'History'];

  let mockMatches = [
    { name: 'John Doe', interests: ['Books', 'Tech'] },
    { name: 'Jane Smith', interests: ['Gardening', 'Fitness'] },
    { name: 'Alex Jones', interests: ['Cooking', 'History'] },
  ];

  // Toggle the selected interest (add/remove from the array)
  function toggleInterest(interest) {
    if (selectedInterests.includes(interest)) {
      selectedInterests = selectedInterests.filter(i => i !== interest);
    } else {
      selectedInterests = [...selectedInterests, interest];
    }
  }

  // Find matches based on selected interests
  function findMatches() {
    return mockMatches.filter(match => 
      match.interests.some(interest => selectedInterests.includes(interest))
    );
  }

  // Start matching function (simulates a match)
  function startMatching() {
    isMatching = true;
    matchFound = false;  // Reset matchFound before starting matching

    // Simulate a matching process with a timeout
    setTimeout(() => {
      const matches = findMatches(); // Get matching results
      matchFound = matches.length > 0; // If matches found, set matchFound to true

      if (matchFound) {
        // If matches are found, store them for display
        mockMatches = matches;
      }
      
      isMatching = false; // Stop the matching process after timeout
    }, 2000); // Adjusted timeout to 2 seconds for quicker testing
  }

  // Go back to the interests selection (reset the matching state)
  function goBackToChat() {
    isMatching = false;
    matchFound = false;
    selectedInterests = [];  // Optionally reset the selected interests too
    mockMatches = [
      { name: 'John Doe', interests: ['Books', 'Tech'] },
      { name: 'Jane Smith', interests: ['Gardening', 'Fitness'] },
      { name: 'Alex Jones', interests: ['Cooking', 'History'] },
    ];  // Reset mock matches
  }

</script>

<svelte:head>
  <title>NeighborLink - Coffee Chat</title>
</svelte:head>

<div class="max-w-2xl mx-auto text-center" in:fade>
  <h1 class="text-3xl font-bold text-center pt-12 pb-8">Coffee Chat</h1>
  <p class="text-lg mb-8">Connect with a random community member for a casual 1-on-1 chat!</p>

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
      {#if matchFound}
        <p class="text-xl mb-4">Match found! Check out the matches below:</p>
        {#each mockMatches as match}
          <div class="bg-gray-100 p-4 mb-4 rounded-md flex items-center">
            <div>
              <p class="font-semibold text-left hover:text-blue-600 hover:underline">{match.name}</p>
              <p>{match.interests.join(', ')}</p>
            </div>
          </div>
        {/each}
      {:else}
        <p class="text-xl mb-4">No matches found. Try selecting different interests.</p>
      {/if}
      <!-- Back Button -->
      <button on:click={goBackToChat} class="mt-4 text-blue-600 hover:underline">
        ← Back to Chat Page
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
