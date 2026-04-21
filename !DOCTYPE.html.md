<!DOCTYPE html>  
<html lang="pt-br">  
<head>  
<meta charset="UTF-8">  
<title>Excel Pro | Treinamento</title>  
  
<style>  
body {  
  margin: 0;  
  font-family: Arial;  
  background: #0f172a;  
  color: #e2e8f0;  
  display: flex;  
}  
  
.sidebar {  
  width: 220px;  
  background: #020617;  
  height: 100vh;  
  padding: 20px;  
}  
  
.sidebar h2 {  
  color: #38bdf8;  
}  
  
.sidebar button {  
  width: 100%;  
  margin: 10px 0;  
  padding: 10px;  
  background: #1e293b;  
  border: none;  
  color: white;  
  cursor: pointer;  
}  
  
.sidebar button:hover {  
  background: #334155;  
}  
  
.main {  
  flex: 1;  
  padding: 20px;  
}  
  
.card {  
  background: #1e293b;  
  padding: 20px;  
  margin-bottom: 20px;  
  border-radius: 10px;  
}  
  
code {  
  display: block;  
  background: black;  
  padding: 10px;  
  margin-top: 10px;  
}  
  
button.copy {  
  margin-top: 10px;  
  background: #38bdf8;  
  border: none;  
  padding: 8px;  
  cursor: pointer;  
}  
  
input {  
  padding: 10px;  
  width: 100%;  
  margin-top: 10px;  
}  
  
.result-ok {  
  color: #22c55e;  
  font-weight: bold;  
}  
  
.result-risk {  
  color: #ef4444;  
  font-weight: bold;  
}  
</style>  
</head>  
  
<body>  
  
<div class="sidebar">  
<h2>Excel Pro</h2>  
<button onclick="show('aulas')">📘 Aulas</button>  
<button onclick="show('exercicio')">🧠 Exercício</button>  
<button onclick="show('simulador')">⚠️ Simulador</button>  
</div>  
  
<div class="main">  
  
<div id="aulas">  
<div class="card">  
<h3>PROCX</h3>  
<code id="f1">=PROCX(A2; Base!A:A; Base!B:B)</code>  
<button class="copy" onclick="copy('f1')">Copiar</button>  
</div>  
  
<div class="card">  
<h3>SE + E</h3>  
<code id="f2">=SE(E(B2>1000; C2="Internacional"); "Fraude"; "OK")</code>  
<button class="copy" onclick="copy('f2')">Copiar</button>  
</div>  
  
<div class="card">  
<h3>SOMASES</h3>  
<code id="f3">=SOMASES(C:C; B:B; "Fraude")</code>  
<button class="copy" onclick="copy('f3')">Copiar</button>  
</div>  
</div>  
  
<div id="exercicio" style="display:none;">  
<div class="card">  
<h3>Desafio</h3>  
<p>Classifique valores acima de 1000 como "Alto".</p>  
<input id="resposta">  
<button onclick="verificar()">Verificar</button>  
<p id="feedback"></p>  
</div>  
</div>  
  
<div id="simulador" style="display:none;">  
<div class="card">  
<h3>Análise de Fraude</h3>  
  
<label>Valor:</label>  
<input id="valor">  
  
<label>País:</label>  
<input id="pais">  
  
<button onclick="analisar()">Analisar</button>  
  
<p id="resultado"></p>  
  
</div>  
</div>  
  
</div>  
  
<script>  
function show(id){  
  document.getElementById('aulas').style.display='none';  
  document.getElementById('exercicio').style.display='none';  
  document.getElementById('simulador').style.display='none';  
  document.getElementById(id).style.display='block';  
}  
  
function copy(id){  
  let text = document.getElementById(id).innerText;  
  navigator.clipboard.writeText(text);  
  alert("Copiado!");  
}  
  
function verificar(){  
  let r = document.getElementById('resposta').value;  
  if(r.includes("SE")){  
    document.getElementById('feedback').innerText="✔ Correto";  
    document.getElementById('feedback').className="result-ok";  
  } else {  
    document.getElementById('feedback').innerText="✖ Use SE";  
    document.getElementById('feedback').className="result-risk";  
  }  
}  
  
function analisar(){  
  let valor = document.getElementById('valor').value;  
  let pais = document.getElementById('pais').value;  
  
  if(valor > 1000 && pais != "Brasil"){  
    document.getElementById('resultado').innerText="🚨 Alto Risco";  
    document.getElementById('resultado').className="result-risk";  
  } else {  
    document.getElementById('resultado').innerText="✅ Normal";  
    document.getElementById('resultado').className="result-ok";  
  }  
}  
</script>  
  
</body>  
</html>  
