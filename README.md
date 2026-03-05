<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Chatbot IA da Alura</title>
  <style>
    body { font-family: Arial, sans-serif; background: #f0f0f0; text-align: center; padding: 50px; }
    #chatbox { width: 100%; max-width: 500px; margin: 0 auto; background: #fff; padding: 20px; border-radius: 10px; }
    input { width: 80%; padding: 10px; margin-top: 10px; }
    button { padding: 10px; }
    #messages { margin-top: 20px; text-align: left; }
    .user { color: blue; }
    .bot { color: green; }
  </style>
</head>
<body>
  <h1>Chatbot IA da Alura</h1>
  <div id="chatbox">
    <div id="messages">
      <div class="bot">Olá! Qual é o seu nome?</div>
    </div>
    <input type="text" id="userInput" placeholder="Digite aqui..." />
    <button onclick="sendMessage()">Enviar</button>
  </div>

  <script>
    let stage = 0;
    let userName = '';

    function sendMessage() {
      const input = document.getElementById('userInput');
      const message = input.value.trim();
      if (!message) return;

      const messagesDiv = document.getElementById('messages');
      messagesDiv.innerHTML += `<div class="user">Você: ${message}</div>`;

      if (stage === 0) {
        userName = message;
        messagesDiv.innerHTML += `<div class="bot">Olá, ${userName}! Escolha um número de 1 a 10:</div>`;
        stage++;
      } else if (stage === 1) {
        const num = parseInt(message);
        if (isNaN(num) || num < 1 || num > 10) {
          messagesDiv.innerHTML += `<div class="bot">Por favor, escolha um número entre 1 e 10.</div>`;
        } else {
          if (num % 2 === 0) {
            messagesDiv.innerHTML += `<div class="bot">Interessante! Você gosta de coisas organizadas e lógicas!</div>`;
          } else {
            messagesDiv.innerHTML += `<div class="bot">Legal! Você é criativo e gosta de desafios!</div>`;
          }
          messagesDiv.innerHTML += `<div class="bot">Obrigado por interagir com o Chatbot IA!</div>`;
          stage++;
        }
      }

      input.value = '';
      input.focus();
      messagesDiv.scrollTop = messagesDiv.scrollHeight;
    }

    document.getElementById('userInput').addEventListener("keypress", function(e) {
      if (e.key === "Enter") sendMessage();
    });
  </script>
</body>
</html>
