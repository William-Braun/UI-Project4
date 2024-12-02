<script>
   import { Link } from "svelte-routing";
 </script>
 
 <section class="hero">
   <div class="container">
     <h2>Welcome to Your Digital Neighborhood</h2>
     <p>Connect, share, and grow with your local community and beyond.</p>
     <Link to="/signup" class="cta-button">Join NeighborLink</Link>
   </div>
 </section>
 
 <section class="features">
   <div class="container">
     <h3>Discover Our Features</h3>
     <div class="feature-grid">
       {#each [
         { title: "Virtual Spaces", icon: "👥", description: "Join topic-based rooms and connect with like-minded individuals.", link: "/spaces" },
         { title: "Coffee Chats", icon: "☕", description: "Have spontaneous 1-on-1 video calls with community members.", link: "/chat" },
         { title: "Local Events", icon: "📅", description: "Discover and join events happening in your area.", link: "/events" },
         { title: "Community Forums", icon: "📚", description: "Engage in ongoing, structured discussions on various topics.", link: "/forums" }
       ] as feature}
         <div class="feature-card">
           <span class="feature-icon">{feature.icon}</span>
           <h4>{feature.title}</h4>
           <p>{feature.description}</p>
           <Link to={feature.link}>Learn More</Link>
         </div>
       {/each}
     </div>
   </div>
 </section>
 
 <section class="events">
   <div class="container">
     <h3>Upcoming Events</h3>
     <div class="event-grid">
       {#each [
         { title: "Virtual Book Club", date: "Dec 10, 2023", attendees: 15 },
         { title: "Local Gardening Workshop", date: "Dec 12, 2023", attendees: 8 },
         { title: "Community Game Night", date: "Dec 15, 2023", attendees: 20 }
       ] as event}
         <div class="event-card">
           <h4>{event.title}</h4>
           <p class="event-date">{event.date}</p>
           <p>{event.attendees} attendees</p>
           <button class="rsvp-button">RSVP</button>
         </div>
       {/each}
     </div>
   </div>
 </section>
 
 <style>
   .container {
     max-width: 1200px;
     margin: 0 auto;
     padding: 0 1rem;
   }
 
   .hero {
     background-color: #f0f0f0;
     padding: 4rem 0;
     text-align: center;
   }
 
   .hero h2 {
     font-size: 2.5rem;
     margin-bottom: 1rem;
   }
 
   .hero p {
     font-size: 1.2rem;
     margin-bottom: 2rem;
   }
 
   .cta-button {
     display: inline-block;
     background-color: #3498db;
     color: white;
     padding: 0.75rem 1.5rem;
     border-radius: 4px;
     text-decoration: none;
     font-weight: bold;
     transition: background-color 0.3s;
   }
 
   .cta-button:hover {
     background-color: #2980b9;
   }
 
   .features, .events {
     padding: 4rem 0;
   }
 
   .features h3, .events h3 {
     font-size: 2rem;
     text-align: center;
     margin-bottom: 2rem;
   }
 
   .feature-grid, .event-grid {
     display: grid;
     grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
     gap: 2rem;
   }
 
   .feature-card, .event-card {
     background-color: white;
     border-radius: 8px;
     padding: 1.5rem;
     box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
   }
 
   .feature-icon {
     font-size: 2rem;
     margin-bottom: 1rem;
     display: block;
   }
 
   .feature-card h4, .event-card h4 {
     font-size: 1.2rem;
     margin-bottom: 0.5rem;
   }
 
   .feature-card p, .event-card p {
     margin-bottom: 1rem;
   }
 
   .feature-card a {
     color: #3498db;
     text-decoration: none;
   }
 
   .event-date {
     color: #666;
     font-style: italic;
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
     .hero h2 {
       font-size: 2rem;
     }
 
     .hero p {
       font-size: 1rem;
     }
 
     .feature-grid, .event-grid {
       grid-template-columns: 1fr;
     }
   }
 </style>
 
 