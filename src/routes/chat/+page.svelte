<script>
    import { onMount } from 'svelte';
    import { FaPaperPlane } from 'svelte-icons/fa';
  
    let messages = [
      { sender: 'John', message: "Hey, how are you?" },
      { sender: 'You', message: "I'm doing great, thanks! How about you?" },
      { sender: 'John', message: "I'm good too. Did you hear about the community event next week?" },
      { sender: 'You', message: "No, I haven't. What's happening?" },
      { sender: 'John', message: "There's a neighborhood cleanup drive. Want to join?" },
      { sender: 'You', message: "Sounds great! Count me in." },
    ];
  
    let newMessage = '';
    let chatContainer;
  
    function handleSend() {
      if (newMessage.trim()) {
        messages = [...messages, { sender: 'You', message: newMessage }];
        newMessage = '';
      }
    }
  
    onMount(() => {
      chatContainer.scrollTop = chatContainer.scrollHeight;
    });
  
    $: {
      if (chatContainer) {
        chatContainer.scrollTop = chatContainer.scrollHeight;
      }
    }
  </script>
  
  <div class="container">
    <h1>Chat</h1>
    <div class="chat-container">
      <div class="chat-header">
        <h2>Chat with John</h2>
        <p>Last active 5 minutes ago</p>
      </div>
      <div class="chat-messages" bind:this={chatContainer}>
        {#each messages as msg}
          <div class="message {msg.sender === 'You' ? 'sent' : 'received'}">
            <div class="message-content">
              {msg.message}
            </div>
          </div>
        {/each}
      </div>
      <div class="chat-input">
        <input 
          type="text" 
          bind:value={newMessage} 
          placeholder="Type a message..." 
          on:keypress={(e) => e.key === 'Enter' && handleSend()}
        />
        <button on:click={handleSend} class="send-button">
          <svelte:component this={FaPaperPlane} />
        </button>
      </div>
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
  
    .chat-container {
      background-color: white;
      border-radius: 8px;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
      overflow: hidden;
    }
  
    .chat-header {
      background-color: #3498db;
      color: white;
      padding: 1rem;
    }
  
    .chat-header h2 {
      margin: 0;
      font-size: 1.2rem;
    }
  
    .chat-header p {
      margin: 0;
      font-size: 0.9rem;
      opacity: 0.8;
    }
  
    .chat-messages {
      height: 400px;
      overflow-y: auto;
      padding: 1rem;
    }
  
    .message {
      margin-bottom: 1rem;
      display: flex;
    }
  
    .message-content {
      padding: 0.5rem 1rem;
      border-radius: 20px;
      max-width: 70%;
    }
  
    .sent {
      justify-content: flex-end;
    }
  
    .sent .message-content {
      background-color: #3498db;
      color: white;
    }
  
    .received .message-content {
      background-color: #f1f0f0;
    }
  
    .chat-input {
      display: flex;
      padding: 1rem;
      border-top: 1px solid #e0e0e0;
    }
  
    .chat-input input {
      flex-grow: 1;
      padding: 0.5rem;
      border: 1px solid #ccc;
      border-radius: 4px;
      margin-right: 0.5rem;
    }
  
    .send-button {
      background-color: #3498db;
      color: white;
      border: none;
      border-radius: 4px;
      padding: 0.5rem 1rem;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
    }
  
    .send-button :global(svg) {
      width: 16px;
      height: 16px;
    }
  
    @media (max-width: 768px) {
      .chat-messages {
        height: 300px;
      }
    }
  </style>
  
  