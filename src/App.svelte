<script>
  import { Router, Route, Link } from "svelte-routing";
  import MenuBar from "./components/MenuBar.svelte";
  import Home from "./routes/Home.svelte";
  import Spaces from "./routes/Spaces.svelte";
  import Events from "./routes/Events.svelte";
  import Chat from "./routes/Chat.svelte";

  // Get the current path
  let path = window.location.pathname;
</script>

<Router {path}>
  <div class="app-container">
    <MenuBar />
    <main>
      <Route path="/" component={Home} />
      <Route path="/spaces" component={Spaces} />
      <Route path="/events" component={Events} />
      <Route path="/chat" component={Chat} />
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
</Router>

<style>
  :global(body) {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    background-color: #f8f9fa;
    color: #333;
  }

  .app-container {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }

  main {
    flex-grow: 1;
    padding: 20px;
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

