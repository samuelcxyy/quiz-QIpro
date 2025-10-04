# quiz-QIpro
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<title>Quiz de QI Profissional</title>
<style>
  body { font-family: Arial, sans-serif; padding: 20px; background-color:#f5f5f5; }
  h1 { text-align: center; }
  .question { margin-bottom: 20px; }
  input[type="text"] { width: 100%; padding: 8px; }
  button { padding: 10px 20px; font-size: 16px; cursor: pointer; }
  .hidden { display: none; }
  #waitPage, #resultPage { text-align: center; margin-top: 50px; }
  textarea { width: 100%; height: 60px; }
</style>
</head>
<body>

<h1>Quiz de QI Profissional</h1>

<form id="quizForm">
  <div class="question">
    <label>1. Qual é 2 + 2?</label><br>
    <input type="text" name="q1">
  </div>
  <div class="question">
    <label>2. Qual é a capital do Brasil?</label><br>
    <input type="text" name="q2">
  </div>
  <div class="question">
    <label>3. Complete: A água congela a ___°C?</label><br>
    <input type="text" name="q3">
  </div>
  <div class="question">
    <label>4. Qual é a forma geométrica com 3 lados?</label><br>
    <input type="text" name="q4">
  </div>
  <div class="question">
    <label>5. Se João tem 5 maçãs e come 2, quantas sobraram?</label><br>
    <input type="text" name="q5">
  </div>
  <button type="button" onclick="submitQuiz()">Enviar</button>
</form>

<div id="waitPage" class="hidden">
  <h2>Já está quase lá!!</h2>
  <p>A partir de R$0,25 você terá seu resultado</p>
  <textarea readonly>00020126360014br.gov.bcb.pix0114+552199119206552040000530398654040.255802BR5925Samuel Cordeiro de Araujo6009Sao Paulo610901227-20062240520daqr107764083530264763049D56</textarea>
</div>

<div id="resultPage" class="hidden">
  <h2>Resultados do Quiz</h2>
  <p id="answers"></p>
  <p id="qiLevel"></p>
</div>

<script>
let quizSubmitted = false;

function submitQuiz() {
  quizSubmitted = true;
  document.getElementById('quizForm').classList.add('hidden');
  document.getElementById('waitPage').classList.remove('hidden');

  // Aguarda 1 minuto antes de mostrar resultado
  setTimeout(showResults, 60000);
}

function showResults() {
  document.getElementById('waitPage').classList.add('hidden');
  document.getElementById('resultPage').classList.remove('hidden');

  const form = document.getElementById('quizForm');
  
  const answers = [
    "1: " + form.q1.value,
    "2: " + form.q2.value,
    "3: " + form.q3.value,
    "4: " + form.q4.value,
    "5: " + form.q5.value
  ].join("<br>");
  
  document.getElementById('answers').innerHTML = `<strong>Suas respostas:</strong><br>${answers}`;

  // Sistema detalhado de pontos
  let score = 0;

  if(form.q1.value.trim() === "4") score += 20;
  if(form.q2.value.trim().toLowerCase() === "brasília") score += 20;
  if(form.q3.value.trim() === "0") score += 20;
  if(form.q4.value.trim().toLowerCase() === "triângulo") score += 20;
  if(form.q5.value.trim() === "3") score += 20;

  // Conversão detalhada em QI
  let qi;
  if(score === 100) qi = "QI Muito Alto (130+)";
  else if(score >= 80) qi = "QI Alto (115-129)";
  else if(score >= 60) qi = "QI Médio (90-114)";
  else if(score >= 40) qi = "QI Baixo (70-89)";
  else qi = "QI Muito Baixo (<70)";

  document.getElementById('qiLevel').innerHTML = `<strong>Nível de QI:</strong> ${qi}`;
}
</script>

</body>
</html>
