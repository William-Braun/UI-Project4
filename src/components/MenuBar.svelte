<script>
   import { Link } from "svelte-routing";
 </script>
 
 <header>
   <div class="container">
     <Link to="/" class="logo">NeighborLink</Link>
     <nav>
       <ul>
         <li><Link to="/">Home</Link></li>
         <li><Link to="/spaces">Spaces</Link></li>
         <li><Link to="/events">Events</Link></li>
         <li><Link to="/chat">Chat</Link></li>
       </ul>
     </nav>
   </div>
 </header>
 
 <style>
   header {
     background-color: #3498db;
     color: white;
     padding: 1rem 0;
   }
 
   .container {
     max-width: 1200px;
     margin: 0 auto;
     display: flex;
     justify-content: space-between;
     align-items: center;
   }
 
   .logo {
     font-size: 1.5rem;
     font-weight: bold;
     text-decoration: none;
     color: white;
   }
 
   nav ul {
     list-style-type: none;
     display: flex;
     gap: 1rem;
   }
 
   nav a {
     text-decoration: none;
     color: white;
     padding: 0.5rem 1rem;
     border-radius: 4px;
     transition: background-color 0.3s;
   }
 
   nav a:hover {
     background-color: rgba(255, 255, 255, 0.2);
   }
 
   @media (max-width: 768px) {
     .container {
       flex-direction: column;
       align-items: flex-start;
     }
 
     nav ul {
       margin-top: 1rem;
     }
   }
 </style>
 
 