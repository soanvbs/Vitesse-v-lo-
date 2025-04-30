<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Simulation Cycliste Avancée</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 40px;
      background: #f9f9f9;
    }
    .slider-container {
      margin-bottom: 25px;
    }
    label {
      display: block;
      margin-bottom: 5px;
    }
    .output {
      font-weight: bold;
      color: #003366;
    }
    h1 {
      color: #005a8d;
    }
  </style>
</head>
<body>

  <h1>Simulation Cycliste Avancée</h1>

  <div class="slider-container">
    <label for="vitesseSolo">Vitesse en vélo solo (km/h): <span id="valVitesseSolo" class="output">30</span></label>
    <input type="range" id="vitesseSolo" min="20" max="40" value="30">
  </div>

  <div class="slider-container">
    <label for="taillePeloton">Taille du peloton: <span id="valTaillePeloton" class="output">10</span></label>
    <input type="range" id="taillePeloton" min="1" max="50" value="10">
  </div>

  <div class="slider-container">
    <label>Vitesse estimée en peloton (km/h): <span id="valVitessePeloton" class="output">0</span></label>
  </div>

  <script>
    const vitesseSolo = document.getElementById('vitesseSolo');
    const taillePeloton = document.getElementById('taillePeloton');
    const valVitesseSolo = document.getElementById('valVitesseSolo');
    const valTaillePeloton = document.getElementById('valTaillePeloton');
    const valVitessePeloton = document.getElementById('valVitessePeloton');

    function calculerVitessePeloton() {
      const solo = parseFloat(vitesseSolo.value);
      const taille = parseInt(taillePeloton.value);

      // Formule logarithmique pour le gain
      const gain = 0.05 * Math.log(taille);
      const peloton = solo * (1 + gain);

      valVitessePeloton.textContent = peloton.toFixed(2);
    }

    function updateValues() {
      valVitesseSolo.textContent = vitesseSolo.value;
      valTaillePeloton.textContent = taillePeloton.value;
      calculerVitessePeloton();
    }

    vitesseSolo.addEventListener('input', updateValues);
    taillePeloton.addEventListener('input', updateValues);

    updateValues(); // Initialiser à l'ouverture
  </script>

</body>
</html>
