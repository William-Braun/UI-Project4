<script>
  import { fade } from 'svelte/transition';

  let isMatching = false;
  let matchFound = false;
  let checkFound = false;
  let selectedInterests = [];  // Array to store selected interests
  let userInterests = ['Gardening', 'Books', 'Tech', 'Fitness', 'Cooking', 'History'];

  let mockMatches = [
    { name: 'John Doe', interests: ['Books', 'Tech'] },
    { name: 'Jane Smith', interests: ['Gardening', 'Fitness'] },
    { name: 'Alex Jones', interests: ['Cooking', 'History'] },
  ];

  // Toggle the selected interest
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

  // Start matching function 
  function startMatching() {
    isMatching = true;
    matchFound = false; 
    checkFound = false;
    console.log("Matching started...");

    // Simulate a matching process with a timeout
    setTimeout(() => {
      const matches = findMatches(); 
      if (matches.length > 0) {
        matchFound = true;  
        mockMatches = matches; 
        console.log("Matches found:", matches);
      } else {
        matchFound = false; 
        console.log("No matches found.");
      }

      isMatching = false; 
      checkFound = true;
    }, 2000); // Simulate matching for 2 seconds
  }

  // Go back to the interests selection
  function goBackToChat() {
    isMatching = false;
    matchFound = false;  
    checkFound = false;
    selectedInterests = []; 
    mockMatches = [
      { name: 'John Doe', interests: ['Books', 'Tech'] },
      { name: 'Jane Smith', interests: ['Gardening', 'Fitness'] },
      { name: 'Alex Jones', interests: ['Cooking', 'History'] },
    ];  // Reset mock matches to initial state
    console.log("Back to interests page.");
  }
</script>

<svelte:head>
  <title>NeighborLink - Coffee Chat</title>
</svelte:head>

<div class="max-w-2xl mx-auto text-center" in:fade>
  <h1 class="text-3xl font-bold text-center pt-12 pb-8">Coffee Chat</h1>
  <p class="text-lg mb-8">Connect with a random community member for a casual 1-on-1 chat!</p>

  <div class="bg-white p-8 rounded-lg shadow-md">
    {#if !isMatching && !checkFound} 
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
      {#if matchFound} <!-- When match is found -->
        <p class="text-xl mb-4">Match found! Check out the matches below:</p>
        {#each mockMatches as match}
          <div class="bg-gray-100 p-4 mb-4 rounded-md flex items-center">
            <div>
              <p class="font-semibold text-left hover:text-blue-600 hover:underline">{match.name}</p>
              <p>{match.interests.join(', ')}</p>
            </div>
          </div>
        {/each}
      {:else} <!-- When no match is found -->
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
