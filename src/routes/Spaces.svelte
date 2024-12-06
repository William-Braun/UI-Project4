<script>
  import { FaUsers, FaSearch } from 'svelte-icons/fa';

  const spaces = [
    { name: "Gardening Enthusiasts", members: 1250, description: "Share tips and tricks for growing beautiful gardens." },
    { name: "Book Lovers Club", members: 3000, description: "Discuss your favorite books and discover new reads." },
    { name: "Local Foodies", members: 2100, description: "Explore local cuisine and share restaurant recommendations." },
    { name: "Tech Talk", members: 1800, description: "Stay up-to-date with the latest in technology and gadgets." },
    { name: "Fitness Friends", members: 2500, description: "Motivate each other to stay fit and healthy." },
    { name: "Art & Creativity", members: 1600, description: "Share your artwork and get inspired by others." },
  ];
</script>

<div class="container">
  <h1>Virtual Spaces</h1>
  <div class="search-bar">
    <input type="text" placeholder="Search spaces..." />
    <button class="search-button">
      <svelte:component this={FaSearch} />
      Search
    </button>
  </div>
  <div class="spaces-grid">
    {#each spaces as space}
      <div class="space-card">
        <h2>{space.name}</h2>
        <p class="members"><svelte:component this={FaUsers} /> {space.members} members</p>
        <p>{space.description}</p>
        <button class="join-button">Join Space</button>
      </div>
    {/each}
  </div>
</div>

<style>
  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 2rem 1rem;
  }

  h1 {
    font-size: 2rem;
    margin-bottom: 1rem;
  }

  .search-bar {
    display: flex;
    margin-bottom: 2rem;
  }

  .search-bar input {
    flex-grow: 1;
    padding: 0.5rem;
    border: 1px solid #ccc;
    border-radius: 4px 0 0 4px;
  }

  .search-button {
    display: flex;
    align-items: center;
    padding: 0.5rem 1rem;
    background-color: #3498db;
    color: white;
    border: none;
    border-radius: 0 4px 4px 0;
    cursor: pointer;
  }

  .search-button :global(svg) {
    width: 16px;
    height: 16px;
    margin-right: 0.5rem;
  }

  .spaces-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
  }

  .space-card {
    background-color: white;
    border-radius: 8px;
    padding: 1.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  .space-card h2 {
    font-size: 1.5rem;
    margin-bottom: 0.5rem;
  }

  .members {
    display: flex;
    align-items: center;
    color: #666;
    margin-bottom: 1rem;
  }

  .members :global(svg) {
    width: 16px;
    height: 16px;
    margin-right: 0.5rem;
  }

  .join-button {
    background-color: #3498db;
    color: white;
    border: none;
    padding: 0.5rem 1rem;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s;
  }

  .join-button:hover {
    background-color: #2980b9;
  }

  @media (max-width: 768px) {
    .spaces-grid {
      grid-template-columns: 1fr;
    }
  }
</style>

