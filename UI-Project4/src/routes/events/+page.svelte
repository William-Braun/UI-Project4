<script>
    import { fade, fly } from 'svelte/transition';
  
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
  
  <div class="events-container" in:fade={{ duration: 300 }}>
    <h1>Local Events</h1>
  
    <p>Discover and participate in events happening in your community!</p>
  
    <div class="events-list">
      {#each events as event, index}
        <div class="event-card" in:fly={{ y: 20, duration: 300, delay: index * 100 }}>
          <div class="event-icon">{event.icon}</div>
          <div class="event-details">
            <h2>{event.name}</h2>
            <p>Date: {event.date}</p>
            <p>Time: {event.time}</p>
          </div>
          <button>RSVP</button>
        </div>
      {/each}
    </div>
  </div>
  
  <style>
    .events-container {
      background-color: #ffffff;
      border-radius: 8px;
      padding: 2rem;
      box-shadow: 0 4px 6px rgba(0,0,0,0.1);
    }
  
    h1 {
      color: #2c3e50;
      font-size: 2.5rem;
      margin-bottom: 1rem;
    }
  
    .events-list {
      display: grid;
      gap: 1.5rem;
      margin-top: 2rem;
    }
  
    .event-card {
      background-color: #f8f9fa;
      border-radius: 8px;
      padding: 1.5rem;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
      display: flex;
      align-items: center;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
    }
  
    .event-card:hover {
      transform: translateY(-5px);
      box-shadow: 0 4px 8px rgba(0,0,0,0.15);
    }
  
    .event-icon {
      font-size: 2.5rem;
      margin-right: 1.5rem;
    }
  
    .event-details {
      flex-grow: 1;
    }
  
    h2 {
      color: #3498db;
      font-size: 1.2rem;
      margin-bottom: 0.5rem;
    }
  
    button {
      background-color: #9b59b6;
      color: white;
      border: none;
      padding: 0.5rem 1rem;
      border-radius: 4px;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
  
    button:hover {
      background-color: #8e44ad;
    }
  </style>
  
  