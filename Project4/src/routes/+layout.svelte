<script>
  import '../app.css';
</script>

<div class="app-container">
  <header>
    <nav>
      <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/spaces">Spaces</a></li>
        <li><a href="/events">Events</a></li>
        <li><a href="/chat">Chat</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <slot />
  </main>

  <footer>
    <div class="footer-content">
      <div class="footer-info">
        <h2>NeighborLink</h2>
        <p>Connecting communities, one click at a time.</p>
      </div>
      <div class="newsletter">
        <h3>Stay Connected</h3>
        <form>
          <input type="email" placeholder="Enter your email" />
          <button type="submit">Subscribe</button>
        </form>
      </div>
    </div>
  </footer>
</div>

<style>
  .app-container {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }

  main {
    flex-grow: 1;
    padding: 20px;
  }

  header {
    background-color: #3498db;
    color: white;
    padding: 1rem 0;
  }

  nav ul {
    list-style-type: none;
    display: flex;
    justify-content: center;
    gap: 1rem;
    margin: 0;
    padding: 0;
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

  footer {
    background-color: #3498db;
    color: white;
    padding: 2rem 0;
  }

  .footer-content {
    max-width: 1200px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    padding: 0 1rem;
  }

  .footer-info h2 {
    font-size: 1.5rem;
    margin-bottom: 0.5rem;
  }

  .newsletter h3 {
    margin-bottom: 1rem;
  }

  .newsletter form {
    display: flex;
  }

  .newsletter input {
    padding: 0.5rem;
    border: none;
    border-radius: 4px 0 0 4px;
  }

  .newsletter button {
    padding: 0.5rem 1rem;
    background-color: #2980b9;
    color: white;
    border: none;
    border-radius: 0 4px 4px 0;
    cursor: pointer;
  }

  @media (max-width: 768px) {
    .footer-content {
      flex-direction: column;
      text-align: center;
    }

    .footer-info, .newsletter {
      margin-bottom: 1rem;
    }
  }
</style>

