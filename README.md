<input type="text" id="username" placeholder="Pseudo Fortnite">
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

