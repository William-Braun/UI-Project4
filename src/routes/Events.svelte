<script>
  import { FaCalendar, FaSearch, FaMapPin, FaClock } from 'svelte-icons/fa';

  const events = [
    { name: "Community Cleanup", date: "Dec 15, 2023", time: "9:00 AM", location: "Central Park", attendees: 50 },
    { name: "Local Art Exhibition", date: "Dec 18, 2023", time: "6:00 PM", location: "City Gallery", attendees: 120 },
    { name: "Neighborhood Potluck", date: "Dec 20, 2023", time: "7:00 PM", location: "Community Center", attendees: 80 },
    { name: "Tech Meetup", date: "Dec 22, 2023", time: "6:30 PM", location: "Innovation Hub", attendees: 65 },
    { name: "Holiday Concert", date: "Dec 24, 2023", time: "7:00 PM", location: "Town Square", attendees: 200 },
    { name: "New Year's Eve Party", date: "Dec 31, 2023", time: "9:00 PM", location: "Grand Hotel", attendees: 300 },
  ];
</script>

<div class="container">
  <h1>Local Events</h1>
  <div class="search-bar">
    <input type="text" placeholder="Search events..." />
    <button class="search-button">
      <svelte:component this={FaSearch} />
      Search
    </button>
  </div>
  <div class="events-grid">
    {#each events as event}
      <div class="event-card">
        <h2>{event.name}</h2>
        <p class="event-info"><svelte:component this={FaCalendar} /> {event.date}</p>
        <p class="event-info"><svelte:component this={FaClock} /> {event.time}</p>
        <p class="event-info"><svelte:component this={FaMapPin} /> {event.location}</p>
        <p>{event.attendees} attendees</p>
        <button class="rsvp-button">RSVP</button>
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

  .events-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
  }

  .event-card {
    background-color: white;
    border-radius: 8px;
    padding: 1.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  .event-card h2 {
    font-size: 1.5rem;
    margin-bottom: 0.5rem;
  }

  .event-info {
    display: flex;
    align-items: center;
    color: #666;
    margin-bottom: 0.5rem;
  }

  .event-info :global(svg) {
    width: 16px;
    height: 16px;
    margin-right: 0.5rem;
  }

  .rsvp-button {
    background-color: #3498db;
    color: white;
    border: none;
    padding: 0.5rem 1rem;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s;
  }

  .rsvp-button:hover {
    background-color: #2980b9;
  }

  @media (max-width: 768px) {
    .events-grid {
      grid-template-columns: 1fr;
    }
  }
</style>

