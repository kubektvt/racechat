
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>ComfyJS Race Chat Overlay</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Orbitron&display=swap');

    body {
      margin: 0;
      padding: 0;
      background: transparent;
      font-family: 'Orbitron', sans-serif;
      color: white;
    }

    .race-chat {
      width: 100%;
      padding: 10px;
      box-sizing: border-box;
    }

    .message {
      display: flex;
      align-items: center;
      margin-bottom: 10px;
      animation: slideIn 0.4s ease forwards;
    }

    .avatar {
      font-size: 26px;
      margin-right: 10px;
      filter: drop-shadow(0 0 4px #ff3c00);
    }

    .text {
      background: #1e1e1e;
      padding: 8px 14px;
      border-radius: 20px;
      box-shadow: 0 0 8px #ff3c00;
      max-width: 75%;
      word-wrap: break-word;
    }

    .user .text {
      background: #ff3c00;
      color: #121212;
      box-shadow: 0 0 10px #ff3c00;
    }

    @keyframes slideIn {
      from {
        opacity: 0;
        transform: translateX(-30px);
      }
      to {
        opacity: 1;
        transform: translateX(0);
      }
    }
  </style>
  <script src="https://unpkg.com/comfy.js@latest/dist/comfy.min.js"></script>
</head>
<body>
  <div class="race-chat" id="chat">
    <!-- Twitch messages will appear here -->
  </div>

  <script>
    function addMessage(username, text, emoji = "🏁") {
      const chat = document.getElementById("chat");
      const message = document.createElement("div");
      message.className = "message user";

      const avatar = document.createElement("div");
      avatar.className = "avatar";
      avatar.textContent = emoji;

      const messageText = document.createElement("div");
      messageText.className = "text";
      messageText.innerText = `${username}: ${text}`;

      message.appendChild(avatar);
      message.appendChild(messageText);
      chat.appendChild(message);

      chat.scrollTop = chat.scrollHeight;
    }

    ComfyJS.onChat = (user, message, flags, self, extra) => {
      addMessage(user, message);
    };

    ComfyJS.Init("kubektvt"); // 
  </script>
</body>
</html>

