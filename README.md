# Escape-box-Athena
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Cadeado de 5 dígitos</title>
  <style>
    body {
      background-color: white; /* Fundo branco agora */
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 20px;
    }

    .hidden { display: none; }

    .container {
      max-width: 600px;
      margin: auto;
      background: white;
      padding: 30px;
      border-radius: 20px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      position: relative;
    }

    h1 {
      margin-bottom: 20px;
    }

    #createInputs input,
    #lockInputs input {
      width: 50px;
      height: 50px;
      font-size: 24px;
      margin: 5px;
      text-align: center;
      border: 2px solid #ccc;
      border-radius: 10px;
    }

    button {
      margin-top: 20px;
      padding: 10px 20px;
      font-size: 18px;
      border: none;
      border-radius: 10px;
      background-color: #4CAF50;
      color: white;
      cursor: pointer;
    }

    button:hover {
      background-color: #45a049;
    }

    #message {
      margin-top: 20px;
      font-size: 20px;
    }

    .side-image {
      position: absolute;
      right: -160px; /* empurra mais pra direita pra caber */
      top: 30px;
      width: 300px; /* coruja ficou 3x maior */
    }

    .top-image {
      width: 80px;
      position: absolute;
      top: -20px;
    }

    .top-left {
      left: -30px;
    }

    .top-right {
      right: -30px;
    }
  </style>
</head>
<body>

  <!-- Página de criação do código -->
  <div id="createCodePage" class="container">
    <h1>Crie seu Código Secreto 🔐</h1>
    <img src="Design%20sem%20nome%20(1).png" class="side-image" alt="Coruja Detetive">
    <div id="createInputs">
      <input id="new1" type="number" min="0" max="9">
      <input id="new2" type="number" min="0" max="9">
      <input id="new3" type="number" min="0" max="9">
      <input id="new4" type="number" min="0" max="9">
      <input id="new5" type="number" min="0" max="9">
    </div>
    <button onclick="saveCode()">Salvar Código</button>
  </div>

  <!-- Página do cadeado -->
  <div id="lockPage" class="container hidden">
    <img src="Design%20sem%20nome%20(2).png" class="top-image top-left" alt="Interrogação">
    <img src="Design%20sem%20nome%20(1).png" class="side-image" alt="Coruja Detetive">
    <h1>Destrave o Cadeado 🔒</h1>
    <div id="lockInputs">
      <input id="lock1" type="number" min="0" max="9">
      <input id="lock2" type="number" min="0" max="9">
      <input id="lock3" type="number" min="0" max="9">
      <input id="lock4" type="number" min="0" max="9">
      <input id="lock5" type="number" min="0" max="9">
    </div>
    <button onclick="unlock()">Destrancar</button>
    <button onclick="createNewCode()" style="background-color: #2196F3; margin-left:10px;">Criar Novo Código</button>
    <p id="message"></p>
  </div>

  <script>
    let savedCode = [];

    function saveCode() {
      savedCode = [
        document.getElementById('new1').value,
        document.getElementById('new2').value,
        document.getElementById('new3').value,
        document.getElementById('new4').value,
        document.getElementById('new5').value
      ];

      if (savedCode.includes("")) {
        alert("Preencha todos os dígitos!");
        return;
      }

      document.getElementById('createCodePage').classList.add('hidden');
      document.getElementById('lockPage').classList.remove('hidden');
    }

    function unlock() {
      const attempt = [
        document.getElementById('lock1').value,
        document.getElementById('lock2').value,
        document.getElementById('lock3').value,
        document.getElementById('lock4').value,
        document.getElementById('lock5').value
      ];

      if (attempt.join('') === savedCode.join('')) {
        document.getElementById('message').textContent = "🔓 Cadeado destrancado!";
        document.getElementById('message').style.color = "green";
      } else {
        document.getElementById('message').textContent = "❌ Código errado, tente novamente!";
        document.getElementById('message').style.color = "red";
      }
    }

    function createNewCode() {
      // Limpa inputs
      document.getElementById('new1').value = '';
      document.getElementById('new2').value = '';
      document.getElementById('new3').value = '';
      document.getElementById('new4').value = '';
      document.getElementById('new5').value = '';
      document.getElementById('lock1').value = '';
      document.getElementById('lock2').value = '';
      document.getElementById('lock3').value = '';
      document.getElementById('lock4').value = '';
      document.getElementById('lock5').value = '';
      document.getElementById('message').textContent = '';

      document.getElementById('lockPage').classList.add('hidden');
      document.getElementById('createCodePage').classList.remove('hidden');
    }
  </script>

</body>
</html>
