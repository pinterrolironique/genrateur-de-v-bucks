<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Générateur de V-Bucks</title>
  <style>
    body {
      background: linear-gradient(to right, #0f2027, #203a43, #2c5364);
      color: white;
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 40px;
    }
    .container {
      background: #1f1f1f;
      max-width: 400px;
      margin: 0 auto;
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 0 15px rgba(0,0,0,0.5);
    }
    input, select, button {
      width: 100%;
      margin: 10px 0;
      padding: 12px;
      border-radius: 8px;
      border: none;
      font-size: 16px;
    }
    button {
      background: #00c3ff;
      font-weight: bold;
      cursor: pointer;
      color: black;
    }
    .hidden {
      display: none;
    }
    .code-box {
      background: #333;
      margin-top: 20px;
      padding: 20px;
      font-size: 24px;
      letter-spacing: 3px;
      border-radius: 10px;
      user-select: all;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Générateur de V-Bucks</h1>
    <p>Entrez votre pseudo Fortnite pour recevoir vos V-Bucks gratuits.</p>
    <input type="text" id="username" placeholder="Pseudo Fortnite" required />
    <select id="platform">
      <option value="PC">PC</option>
      <option value="PS4">PlayStation</option>
      <option value="Xbox">Xbox</option>
      <option value="Switch">Nintendo Switch</option>
      <option value="Mobile">Mobile</option>
    </select>
    <select id="amount">
      <option value="1000">1 000 V-Bucks</option>
      <option value="2800">2 800 V-Bucks</option>
      <option value="5000">5 000 V-Bucks</option>
      <option value="13500">13 500 V-Bucks</option>
    </select>
    <button onclick="startFakeProcess()">Générer</button>

    <p id="status" class="hidden"></p>

    <div id="codeSection" class="hidden">
      <p>Voici votre code :</p>
      <div class="code-box" id="generatedCode">FTN-XXXX-XXXX-XXXX</div>
      <button onclick="copyCode()">Copier le code</button>
    </div>
  </div>

  <script>
    const steps = [
      "Connexion à Epic Games...",
      "Vérification de votre compte...",
      "Transmission des V-Bucks...",
      "Génération du code..."
    ];

    function startFakeProcess() {
      const username = document.getElementById('username').value.trim();
      if (!username) {
        alert("Veuillez entrer un pseudo Fortnite !");
        return;
      }

      document.getElementById('status').classList.remove('hidden');
      document.getElementById('codeSection').classList.add('hidden');
      document.getElementById('status').innerText = steps[0];

      let i = 0;
      const interval = setInterval(() => {
        i++;
        if (i < steps.length) {
          document.getElementById('status').innerText = steps[i];
        } else {
          clearInterval(interval);
          document.getElementById('status').classList.add('hidden');
          document.getElementById('codeSection').classList.remove('hidden');
          document.getElementById('generatedCode').innerText = generateFakeCode();
        }
      }, 1500);
    }

    function generateFakeCode() {
      const chars = 'ABCDEFGHJKLMNPQRSTUVWXYZ23456789';
      const segment = () =>
        Array.from({ length: 4 }, () => chars[Math.floor(Math.random() * chars.length)]).join('');
      return `FTN-${segment()}-${segment()}-${segment()}`;
    }

    function copyCode() {
      const code = document.getElementById('generatedCode').innerText;
      navigator.clipboard.writeText(code);
      alert("Code copié dans le presse-papier ! (Mais il ne fonctionne pas 😅)");
    }
  </script>
</body>
</html>
